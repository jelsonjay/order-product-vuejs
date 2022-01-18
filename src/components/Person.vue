<template>
	<div>
		<h1>This is theperson desc: {{ name }}</h1>
		<Info />
	</div>
</template>

<script>
import Info from './Info.vue';
export default {
	name: 'Person',
	components: { Info },
	data() {
		return {
			name: 'Jelson Jay'
		};
	}
};
</script>
