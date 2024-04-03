<template>
	<button @click="x = x + 1">{{ x }}</button>
	<button @click="y = y + 1">{{ y }}</button>
	<button @click="obj.count = obj.count + 1">{{ obj }}</button>
	<hr />
	<div>{{ person }}</div>
	<button @click="person.obj.count = person.obj.count + 1">
		{{ person.obj.count }}
	</button>
</template>

<script>
import { reactive, ref, watch } from 'vue';

export default {
	setup() {
		const x = ref(1);
		const y = ref(2);

		const obj = reactive({
			count: 0,
		});

		// watch(
		// 	() => x.value + y.value,
		// 	(sum, oldV) => {
		// 		console.log('sum : ', sum);
		// 		console.log('oldV : ', oldV);
		// 	},
		// );

		// watch([x, y], ([newV, oldV]) => {
		// 	console.log(newV, oldV);
		// });

		// watch(
		// 	() => obj.count,
		// 	(newV, oldV) => {
		// 		console.log(newV, oldV);
		// 	},
		// );

		// watch(obj, (newV, oldV) => {
		// 	console.log(newV, oldV);
		// });

		const person = reactive({
			name: '홍길동',
			age: 30,
			hobby: '운동',
			obj: {
				count: 0,
			},
		});

		// watch(person, newValue => {
		// 	console.log('newValue: ', newValue);
		// });

		// getter 핢수를 사용하게 되면 반환되는 값이 바꿨는지 안바꿨는지만 체크하게 된다.
		watch(
			() => person.obj.count,
			newValue => {
				console.log('newValue: ', newValue);
			},
		);

		return { x, y, obj, person };
	},
};
</script>

<style lang="scss" scoped></style>
