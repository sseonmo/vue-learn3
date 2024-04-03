<template>
	<div class="card">
		<div v-if="$slots.header" class="card-header">
			<slot name="header" header-msg="헤더메시지"></slot>
		</div>
		<div v-if="$slots.default" class="card-body">
			<slot :child-msg hello-msg="안녕하세요"></slot>
		</div>
		<div v-if="hasFooter" class="card-footer text-body-secondary">
			<slot name="footer" footer-msg="푸터메시지"></slot>
		</div>
	</div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
	setup(props, { slots }) {
		const childMsg = ref('자식컴포넌트 메세지');

		const hasFooter = computed(() => !!slots.footer);
		return { childMsg, hasFooter };
	},
};
</script>

<style lang="scss" scoped></style>
