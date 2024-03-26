<template>
	<div>
		<div>
			<p>{{ comment.id }}</p>
			<h2>{{ comment.text }}</h2>
			<p>{{ comment.postId }}</p>
			<nuxt-link to="/comments">Подробнее</nuxt-link>
			<hr />
		</div>
	</div>
</template>

<script setup>
import { useRoute } from "vue-router"
import axios from "axios"
const route = useRoute()

const comment = ref({})

const id = computed(() => route.params.id)
onMounted(async () => {
	try {
		const { data } = await axios.get(
			`http://localhost:3001/comments/${id.value}`
		)
		console.log(data)
		comment.value = data
	} catch (error) {
		console.error("Ошибка при получении данных поста:", error)
		return { comment: null }
	}
})
</script>
