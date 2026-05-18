<script setup lang="ts">
const appConfig = useAppConfig()
useSeoMeta({
	title: '关于',
	description: `关于${appConfig.author.name}——${appConfig.description}`,
})

const layoutStore = useLayoutStore()
layoutStore.setAside(['blog-stats'])
</script>

<template>
<div class="mobile-only">
	<BlogHeader to="/" suffix="关于" tag="h1" />
</div>

<article class="about-article">
	<!-- 头像与名称 -->
	<section class="about-hero">
		<img
			:src="appConfig.author.avatar"
			:alt="appConfig.author.name"
			class="about-avatar"
		>
		<h1>{{ appConfig.author.name }}</h1>
		<p class="about-motto">
			<!-- TODO: 替换为你的一句话介绍 -->
			欢迎光临，期待你的了解(￣▽￣) ノ
		</p>
	</section>

	<!-- 个人介绍 -->
	<section class="about-section">
		<h2>关于我</h2>
		<!-- TODO: 替换为你的自我介绍 -->
		<p>我是一名在读初中生，目前正在主攻学习，无法将编程作为主要兴趣，正在编程入门</p>
	</section>

	<!-- 技能 / 方向 -->
	<section class="about-section">
		<h2>方向</h2>
		<!-- TODO: 替换为你的技能或方向 -->
		<ul>
			<li>想成为开源社区的贡献者</li>
			<li>似乎能看懂基础的报错</li>
			<li>看小说，算吗？</li>
		</ul>
	</section>

	<!-- 联系方式 -->
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
			<!-- TODO: 添加更多联系方式，格式同上 -->
		</ul>
	</section>

	<!-- 其他 -->
	<section class="about-section">
		<h2>关于本站</h2>
		<p>
			本博客使用
			<UtilLink to="https://nuxt.com/">Nuxt</UtilLink>
			搭建，主题为
			<UtilLink to="https://github.com/L33Z22L11/blog-v3">Clarity</UtilLink>。
		</p>
		<!-- TODO: 可以补充建站历程、使用的工具等 -->
	</section>
</article>

<PostComment />
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
