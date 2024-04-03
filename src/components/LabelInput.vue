<template>
	<label class="form-label" style="border: 1px solid black" id="child-id">
		{{ label }}
		<!-- <input v-model="username" type="text" /> -->
		<!-- <input
				:value="modelValue"
				@input="event => $emit('update:modelValue', event.target.value)"
				type="text"
			/> -->
	</label>
	<input type="text" class="form-control" v-model="value" v-bind="$attrs" />
</template>

<script>
import { computed, ssrContextKey } from 'vue';

export default {
	props: ['modelValue', 'label'],
	emits: ['update:modelValue'],
	setup(props, { emit }) {
		const value = computed({
			get() {
				return props.modelValue;
			},
			set(value) {
				emit('update:modelValue', value);
			},
		});
		return { value };
	},
};
</script>

<style lang="scss" scoped></style>
