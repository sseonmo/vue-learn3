<template>
	<main>
		<div class="container py-4">
			<MyButton class="my-button" id="my-button" @click="sayHello"></MyButton>
			<LabelInput label="이름" data-id="id입니다."></LabelInput>
			<hr />
			<FancyButton>
				<span style="color: red">@@@213</span> Click!!!
			</FancyButton>
			<FancyButton v-slot="{ fancyMsg }">{{ fancyMsg }}</FancyButton>
			<FancyButton>
				<template v-slot="{ fancyMsg }">
					{{ fancyMsg }}
				</template>
			</FancyButton>

			<hr />
			<AppCard>
				<!-- <template #[slotArgs]>제목입니다.</template> -->
				<!-- <template #default>내용입니다.</template> -->
				<!-- 암시적으로 Default 슬롯입니다.
				<template #footer>푸터입니다.</template> -->
				<template #header="{ headerMsg }">
					{{ headerMsg }}
				</template>
				<template #default="{ childMsg, helloMsg }">
					디폴트입니다
					{{ msg }}
					<br />
					{{ childMsg }}
					<br />
					{{ helloMsg }}
				</template>
				<template #footer="{ footerMsg }">
					{{ footerMsg }}
				</template>
			</AppCard>
			<hr />
			<AppCard> 게시글입니다. </AppCard>
		</div>
	</main>
</template>

<script>
import MyButton from '@/components/MyButton.vue';
import LabelInput from '@/components/LabelInput.vue';
import FancyButton from '@/components/FancyButton.vue';
import AppCard from '@/components/AppCard.vue';
import { ref } from 'vue';

export default {
	components: {
		MyButton,
		LabelInput,
		FancyButton,
		AppCard,
	},
	setup() {
		const sayHello = () => {
			alert('안녕하세요');
		};

		const slotArgs = ref('header');
		const msg = ref('안녕하세요');
		return { sayHello, slotArgs, msg };
	},
};
</script>

<style lang="scss" scoped></style>
