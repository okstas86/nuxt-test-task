<template>
	<div>
		<h1>{{ post.title }}</h1>
		<p>{{ post.description }}</p>
		<p>Просмотры: {{ post.views }}</p>
		<p>SEO заголовок: {{ post.seo_title }}</p>
		<p>SEO описание: {{ post.seo_description }}</p>
		<p>SEO ключевые слова: {{ post.seo_keywords }}</p>
		<nuxt-link to="/posts">Назад к списку</nuxt-link>
	</div>
</template>

<script setup>
import { useRoute } from "vue-router"
import axios from "axios"
const route = useRoute()

const post = ref({})

const id = computed(() => route.params.id)
onMounted(async () => {
	try {
		const { data } = await axios.get(`http://localhost:3001/posts/${id.value}`)
		console.log(data)
		post.value = data
	} catch (error) {
		console.error("Ошибка при получении данных поста:", error)
		return { post: null }
	}
})
</script>
