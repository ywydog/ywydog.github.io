<script setup lang="ts">
const appConfig = useAppConfig()
const layoutStore = useLayoutStore()
layoutStore.setAside(['blog-stats'])

const { data: post } = await useAsyncData(
	'/about',
	() => queryCollection('content').path('/about').first(),
)

const excerpt = computed(() => post.value?.description || '')

if (post.value) {
	useSeoMeta({
		title: post.value.title,
		ogType: 'article',
		ogImage: post.value.image,
		description: post.value.description,
	})
	layoutStore.setAside(post.value.meta?.aside as WidgetName[] | undefined)
}
else {
	useSeoMeta({
		title: '关于',
		description: `关于${appConfig.author.name}——${appConfig.description}`,
	})
}

if (import.meta.dev) {
	watchEffect(() => {
		layoutStore.setAside(post.value?.meta?.aside as WidgetName[] | undefined)
	})
}
</script>

<template>
<template v-if="post">
	<PostHeader v-bind="post" />
	<PostExcerpt v-if="excerpt" :excerpt />
	<ContentRenderer
		class="article"
		:class="getPostTypeClassName(post?.type, { prefix: 'md' })"
		:value="post"
		tag="article"
	/>

	<PostFooter v-bind="post" />
	<PostSurround />
	<PostComment />
</template>

<template v-else>
	<div class="mobile-only">
		<BlogHeader to="/" suffix="关于" tag="h1" />
	</div>

	<article class="about-article">
		<section class="about-hero">
			<img
				:src="appConfig.author.avatar"
				:alt="appConfig.author.name"
				class="about-avatar"
			>
			<h1>{{ appConfig.author.name }}</h1>
			<p class="about-motto">
				欢迎光临，期待你的了解(￣▽￣) ノ
			</p>
		</section>

		<section class="about-section">
			<h2>关于我</h2>
			<p>我是一名在读初中生，目前正在主攻学习，无法将编程作为主要兴趣，正在编程入门</p>
		</section>

		<section class="about-section">
			<h2>方向</h2>
			<ul>
				<li>想成为开源社区的贡献者</li>
				<li>似乎能看懂基础的报错</li>
				<li>看小说，算吗？</li>
			</ul>
		</section>

		<section class="about-section">
			<h2>联系方式</h2>
			<ul>
				<li>
					<Icon name="tabler:brand-github" />
					<UtilLink to="https://github.com/ywydog">GitHub:ywydog </UtilLink>
				</li>
				<li>
					<Icon name="tabler:mail" />
					<UtilLink :to="`mailto:${appConfig.author.email}`">{{ appConfig.author.email }}</UtilLink>
				</li>
			</ul>
		</section>

		<section class="about-section">
			<h2>关于本站</h2>
			<p>
				本博客使用
				<UtilLink to="https://nuxt.com/">Nuxt</UtilLink>
				搭建，主题为
				<UtilLink to="https://github.com/L33Z22L11/blog-v3">Clarity</UtilLink>。
			</p>
		</section>
	</article>

	<PostComment />
</template>
</template>

<style lang="scss" scoped>
.about-article {
	max-width: 42rem;
	margin: 1rem;
	padding: 0 1rem;
}

.about-hero {
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 0.5rem;
	margin-bottom: 2rem;
	text-align: center;
}

.about-avatar {
	width: 6rem;
	height: 6rem;
	border-radius: 50%;
	object-fit: cover;

	@supports (corner-shape: squircle) {
		corner-shape: superellipse(1.2);
		border-radius: 1.5rem;
	}
}

.about-motto {
	color: var(--c-text-2);
	font-size: 0.95em;
}

.about-section {
	margin: 2rem 0;

	h2 {
		margin-bottom: 0.5rem;
		font-size: 1.15rem;
	}

	ul {
		padding-inline-start: 1.2em;

		li {
			display: flex;
			align-items: center;
			gap: 0.3em;
			margin: 0.3em 0;
		}
	}
}
</style>
