<template>
	<h1>This is test vue: {{ name }}</h1>
</template>

<script>
export default {
	name: 'LifeCycle',
	data() {
		return {
			name: 'LifeCycle'
		};
	},
	created() {
		setTimeout(() => {
			this.name = 'Framework';
		}, 3000);
	},
	mounted() {
		setTimeout(() => {
			this.name = 'Vuejs is a framework';
		}, 2000);
	}
};
</script>
