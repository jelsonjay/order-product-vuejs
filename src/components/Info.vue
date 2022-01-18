<template>
	<div>
		<p v-if="is_work">I'm still looking for a new opportunit</p>
		<p v-else>I have't find anything yet!</p>
		<p>I'm a Front-end Developer</p>
		<ul>
			<li>Html5</li>
			<li>Javascript</li>
			<li>Reactjs</li>
			<li>Next.js</li>
			<li>Gatsby.js</li>
			<li>Vue.js</li>
			<li>Node.js</li>
		</ul>
		<h2 v-if="7 >= 7">SHOW ME!</h2>
		<span v-show="showEmail">{{ email }}</span>
		<p>
			visit our website at <a v-bind:href="link" target="_blank">click here</a>
		</p>
		<Image />
	</div>
</template>
<script>
import Image from './Image.vue';
export default {
	components: { Image },
	name: 'Info',
	data() {
		return {
			is_work: true,
			email: 'example@gmail.com',
			showEmail: true,
			link: 'https://nextjs.org'
		};
	}
};
</script>
