<template>
	<Menu :logo="logoImg" :alt="altTitle" />
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
	},
	data() {
		return {
			logoImg: '/images/logo-p.jpg',
			altTitle: 'Order Pizza'
		};
	}
};
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
body {
	background: #fff;
	font-family: monospace;
}
.main {
	margin: 3.125rem;
	min-height: 19.625rem;
}
h1 {
	text-align: center;
	font-size: 2.764rem;
	font-weight: bold;
	color: #e77669;
}
</style>
