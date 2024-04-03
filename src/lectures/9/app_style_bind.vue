<template>
	<div :style="styleObject">
		<div>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid ullam
			dolore culpa eum dolor dolores, natus suscipit rem veniam hic velit
			labore, consequatur voluptate consectetur. Facilis optio obcaecati ipsa
			autem.
		</div>
		<button @click="fontSize--">-</button>
		<button @click="fontSize++">+</button>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		// const styleObjec = reactive({
		// 	color: 'red',
		// 	fontSize: '13px',
		// });

		const fontSize = ref(13);

		// inline 스타일로 쓸때는 카멜케이스로 써야 한다.
		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});

		return { styleObject, fontSize };
	},
};
</script>

<style lang="scss" scoped></style>
