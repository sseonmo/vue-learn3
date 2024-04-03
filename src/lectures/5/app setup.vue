<template>
	<div>
		<button @click="increment">{{ count }}</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const count = ref(0);

		const increment = () => {
			count.value++;
		};

		return { count, increment };
	},
};
</script>

<style lang="scss" scoped></style>
