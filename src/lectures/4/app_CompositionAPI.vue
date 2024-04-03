<template>
	<div>
		<h2>반응형 메세지</h2>

		<p>{{ reactiveMessage }}</p>

		<button @click="addReactiveMessage">Add Message</button>

		<h2>일반 메세지</h2>
		<p>{{ normalMessage }}</p>
		<button @click="addNormalMessage">Add Message</button>
	</div>
</template>

<script>
import { isRef, onBeforeMount, onMounted, ref } from 'vue';

export default {
	setup() {
		console.log('setup()');
		const reactiveMessage = ref('Hello Reactive Message');
		let normalMessage = 'Hello Normal Message';

		const addReactiveMessage = () => {
			reactiveMessage.value = reactiveMessage.value + '!';
		};

		console.log('isRef(addReactiveMessage) : ', isRef(reactiveMessage));

		const addNormalMessage = () => {
			normalMessage = normalMessage.value + '!';
		};
		console.log('isRef(addNormalMessage : ', isRef(normalMessage));

		onMounted(() => {
			console.log('onMounted');
		});

		onBeforeMount(() => {
			console.log('onBeforeMount');
		});

		return {
			reactiveMessage,
			normalMessage,
			addReactiveMessage,
			addNormalMessage,
		};
	},
};
</script>

<style lang="scss" scoped></style>
