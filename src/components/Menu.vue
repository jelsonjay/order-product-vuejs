<template>
	<div class="menu">
		<router-link to="/" id="logo">
			<img :src="logo" v-bind:alt="alt" class="logo-brand" />
		</router-link>
		<router-link to="/">Home</router-link>
		<router-link to="/order">Order</router-link>
	</div>
</template>

<script>
export default {
	name: 'Menu',
	props: ['logo', 'alt']
};
</script>

<style scoped>
.menu {
	background: #fff;
	border-bottom: 4px solid #758;
	padding: 1rem 2.5rem;
	display: flex;
	justify-content: flex-end;
	align-items: center;
}
#logo {
	margin: auto;
	margin-left: 0;
}
.logo-brand {
	height: 40px;
	width: 60px;
}
.menu a {
	font-size: 1rem;
	text-decoration: none;
	margin: 0.9rem;
	transition: 0.5s;
	font-weight: bold;
}
.menu a:hover {
	color: salmon;
}
</style>
