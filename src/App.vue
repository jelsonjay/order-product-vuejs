<template>
	<Menu />
	<router-view />
	<Footer />
</template>

<script>
import Menu from './components/Menu.vue';
import Footer from './components/Footer.vue';
export default {
	name: 'App',
	components: {
		Menu,
		Footer
	}
};
</script>

<style></style>
