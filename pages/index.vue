<template>
	<div class="container">
		<nuxt-link to="/profile"><button>Профиль</button></nuxt-link>
		<nuxt-link to="/posts"><button>Посты</button></nuxt-link>
		<nuxt-link to="/comments"><button>Комментарии</button></nuxt-link>
	</div>
</template>

<script setup></script>

<style scoped>
.container {
	display: flex;
	gap: 2rem;
}
</style>
