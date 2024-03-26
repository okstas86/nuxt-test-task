<template>
	<div>
		<h1>Список постов</h1>
		<div v-for="post in posts" :key="post.id">
			<h2>{{ post.title }}</h2>
			<p>{{ post.description }}</p>
			<nuxt-link :to="`/posts/${post.id}`">Подробнее</nuxt-link>
			<hr />
		</div>
	</div>
</template>

<script setup>
import { ref, onMounted } from "vue"
import axios from "axios"

const posts = ref([])

onMounted(async () => {
	try {
		const { data } = await axios.get("http://localhost:3001/posts")
		console.log("data:", data)
		posts.value = data
	} catch (error) {
		console.error("Ошибка при получении списка публикаций:", error)
	}
})
</script>
