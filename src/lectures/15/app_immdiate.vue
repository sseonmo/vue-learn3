<template>
	<div>
		<p>{{ msg }}</p>
		<p>{{ reverseMsg }}</p>
		<button @click="msg = msg + '!'">msg</button>
	</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const msg = ref('Hello Vue3');
		const reverseMsg = ref('');

		watch(
			msg,
			newV => {
				reverseMsg.value = newV.split('').reverse().join('');
				console.log(newV.split('').reverse().join(''));
			},
			{ immediate: true },
		);

		return { msg, reverseMsg };
	},
};
</script>

<style lang="scss" scoped></style>
