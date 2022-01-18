<template>
	<img alt="Vue logo" src="./assets/logo.png" />
	<HelloWorld msg="Hello Welcome" />
	<About />
	<Life />
	<Person />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import About from './components/About.vue';
import Life from './components/LifeCycle.vue';
import Person from './components/Person.vue';
export default {
	name: 'App',
	components: {
		HelloWorld,
		About,
		Life,
		Person
	}
};
</script>

<style>
#app {
	font-family: Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	margin-top: 60px;
}
h1 {
	color: #050505;
	font-size: 2.5rem;
}
a {
	color: blue;
	font-size: 1rem;
	font-weight: bolder;
}
</style>
