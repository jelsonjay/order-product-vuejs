<template>
	<div>
		<h1>About Page</h1>
		<p>Name is: {{ name }} he is {{ age }} years old role {{ role }}</p>
	</div>
</template>

<script>
export default {
	name: 'About',
	data() {
		return {
			name: 'Jelson',
			age: 42,
			role: 'Front-end Developer'
		};
	}
};
</script>
