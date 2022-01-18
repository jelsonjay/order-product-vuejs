<template>
	<h1>{{ title }}</h1>
	<img :src="img" :alt="title" />
	<span>{{ description }}</span>
</template>

<script>
export default {
	data() {
		return {
			title: 'Fast Food',
			img: '/images/coffee.webp',
			description: 'Try the free coffee'
		};
	}
};
</script>
