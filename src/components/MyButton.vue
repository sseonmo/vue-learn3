<template>
	<div class="p-3 bg-danger">
		<!-- v-bind="$attrs" -->
		<button type="button" class="btn btn-primary" @click="sayHello">
			My Button
		</button>
		<!-- {{$attrs}} -->
	</div>
</template>

<script>
export default {
	// inheritAttrs: false,
	emits: ['click'],
	setup(props, { emit }) {
		// console.log('context.attr :', context.attrs);
		// console.log('context.attr :', context.attrs.class);
		// console.log('context.attr :', context.attrs.id);
		// console.log('context.attr :', context.attrs.onClick);
		const sayHello = () => {
			emit('click');
		};
		return { sayHello };
	},
};
</script>

<style lang="scss" scoped></style>
