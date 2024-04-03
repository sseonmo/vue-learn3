<template>
	<div>
		<div class="card">
			<div class="card-body">
				<!-- {{ $props }} -->
				<!-- type : news, notice -->
				<span class="badge text-bg-secondary">{{ typeName }}</span>
				<h5 class="card-title red mt-2">{{ title }}</h5>
				<p class="card-text">
					{{ contents }}
				</p>
				<a href="#" class="btn" :class="isLikeClass" @click="toggleLike"
					>좋아요</a
				>
			</div>
		</div>
	</div>
</template>

<script>
import { computed } from 'vue';

console.log('AppCard module');
export default {
	props: {
		type: {
			type: String,
			default: 'news',
			validator: value => {
				return ['news', 'notice'].includes(value);
			},
		},
		title: {
			type: String,
			require: true,
		},
		contents: {
			type: String,
			// require: true,
		},
		isLike: {
			type: Boolean,
			default: false,
		},
		// 객체나 배열과 같은 레퍼런스함수의 default 값을 설정할때는 return 값을 반환하는 팩토리 함수를 선언해야 한다.
		obj: {
			type: Object,
			default: () => ({}),
		},
	},
	emits: ['toggleLike'],
	setup(props, context) {
		// console.log('props.title : ', props.title);
		const isLikeClass = computed(() =>
			props.isLike ? 'btn-danger' : 'btn-outline-danger',
		);

		const typeName = computed(() =>
			props.type === 'news' ? '뉴스' : '공지사항',
		);

		const toggleLike = () => {
			// props.isLike = !props.isLike;
			context.emit('toggleLike');
		};

		return { isLikeClass, typeName, toggleLike };
	},
};
</script>

<style></style>

<!-- export default {
	setup() {
		// const style = useCssModule();
		// console.log('style', style);
		console.log('AppCard setup()');

		const color = ref('green');
		return { color };
	},
};
</script>

<style module>
.red {
	color: v-bind(color) !important;
}
</style> -->

<!-- <style scoped>
.red {
	color: red !important;
}
</style> -->

<!-- <style module="classes">
.red {
	color: red !important;
}
</style> -->
