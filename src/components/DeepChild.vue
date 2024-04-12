<template>
	<div class="card">
		<div class="card-header">Deep Child Component</div>
		<div class="card-body">
			<p>{{ staticMsg }}</p>
			<p>{{ message }}</p>
			<p>{{ count }}</p>
		</div>
	</div>
</template>

<script>
import { inject } from 'vue';

export default {
	setup() {
		const staticMsg = inject('static-message', 'default message');
		const { message, updateMsg } = inject('message');
		updateMsg('!');
		// message.value = message.value + "!";
		const count = inject('count');

		return { staticMsg, message, count };
	},
};
</script>

<style lang="scss" scoped></style>
