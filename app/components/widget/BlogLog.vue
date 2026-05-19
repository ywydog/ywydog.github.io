<script setup lang="ts">
const { timeEstablished } = useAppConfig()

const blogLog = [
    { label: '2026-05-20', value: '博客搭建完成' },
    { label: '2026-05-19', value: '发布第一篇文章' },
	{ label: '2026-05-05', value: '开始搭建博客' },
]
</script>

<template>
<BlogWidget card title="更新日志">
	<ZDlGroup size="large" :items="blogLog" />
</BlogWidget>
</template>
