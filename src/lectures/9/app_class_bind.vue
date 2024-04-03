<template>
	<div>
		<!-- <div class="text" :class="{ active: isActive, 'text-danger': hasError }"> -->
		<!-- <div class="text" :class="classObject">테스트입니다.</div> -->
		<div class="text" :class="[activeClass, errorClass]">테스트입니다.</div>
		<button @click="toggle">toggle</button>
		<button @click="hasError = !hasError">errorToggle</button>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		const isActive = ref(true);
		const hasError = ref(false);

		const toggle = () => {
			isActive.value = !isActive.value;
			// console.log(isActive.value, classObject);
		};

		// const classObject = reactive({
		// 	active: isActive.value && true,
		// 	'text-danger': !isActive.value && true,
		// });

		const classObject = computed(() => {
			return {
				active: isActive.value && true,
				'text-danger': !isActive.value && true,
			};
		});

		const activeClass = ref('active');
		const errorClass = ref('text-danger');

		return { isActive, toggle, hasError, classObject, activeClass, errorClass };
	},
};
</script>

<style scoped>
.active {
	font-weight: 900;
}
.text-danger {
	color: skyblue;
}
</style>
