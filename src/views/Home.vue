<template>
	<Hero />
	<div class="main">
		<h2>Best Fast Food In the Towon</h2>
		<PizzaForm />
	</div>
</template>

<script>
import Hero from '../components/Hero.vue';
import PizzaForm from '../components/PizzaForm.vue';
export default {
	name: 'Home',
	components: {
		Hero,
		PizzaForm
	}
};
</script>

<style scoped>
h2 {
	text-align: center;
	font-size: 2rem;
}
</style>
