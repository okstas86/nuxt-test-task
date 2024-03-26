<template>
	<div>
		<h1>Список комментариев</h1>
		<div v-for="comment in comments" :key="comment.id">
			<p>{{ comment.id }}</p>
			<h2>{{ comment.text }}</h2>
			<p>{{ comment.postId }}</p>
			<nuxt-link :to="`/comments/${comment.id}`">Подробнее</nuxt-link>
			<hr />
		</div>
	</div>
</template>

<script setup>
import { ref, onMounted } from "vue"
import axios from "axios"

const comments = ref([])

onMounted(async () => {
	try {
		const { data } = await axios.get("http://localhost:3001/comments")
		console.log("data:", data)
		comments.value = data
	} catch (error) {
		console.error("Ошибка при получении списка публикаций:", error)
	}
})
</script>
