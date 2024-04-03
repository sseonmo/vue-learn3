<template>
	<div>
		{{ message }}
	</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const message = ref('accc');

		watch(message, (newV, oldV) => {
			console.log('newV', newV);
			console.log('oldV', oldV);
		});
		return { message };
	},
};
</script>

<style lang="scss" scoped></style>
