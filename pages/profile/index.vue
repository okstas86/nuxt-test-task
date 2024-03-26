<template>
	<div>
		<h1>Профиль</h1>

		<h2>{{ profiles.name }}</h2>

		<hr />
	</div>
</template>

<script setup>
import { ref, onMounted } from "vue"
import axios from "axios"

const profile = ref({})

onMounted(async () => {
	try {
		const { data } = await axios.get("http://localhost:3001/profile")

		profiles.value = data
	} catch (error) {
		console.error("Ошибка при получении списка публикаций:", error)
	}
})
</script>
