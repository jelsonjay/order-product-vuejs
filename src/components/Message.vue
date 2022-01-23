<template>
	<div class="msg-wrapper">
		<p>{{ msg }}</p>
	</div>
</template>

<script>
export default {
	name: 'Message',
	props: {
		msg: String
	}
};
</script>

<style scoped>
.msg-wrapper {
	background: hsl(115, 55%, 67%);
	color: #fff;
	border: 0;
	margin: 2rem auto;
	padding: 0.8rem;
	max-width: 25rem;
	border-radius: 0.5rem;
	font-weight: bold;
}
</style>
