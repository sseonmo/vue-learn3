<template>
	<div>
		<main>
			<div class="container py-4">
				<PostCreate @create-post="createPost"></PostCreate>

				<hr class="my-4" />

				<div class="container text-center">
					<div class="row g-5">
						<div v-for="post in posts" :key="post.id" class="col col-4">
							<PostItem
								:title="post.title"
								:contents="post.contents"
								:is-like="post.isLike"
								:type="post.type"
								@toggle-like="post.isLike = !post.isLike"
							></PostItem>
							<button @click="post.isLike = !post.isLike">toggle</button>
						</div>
					</div>
				</div>
				<hr class="my-4" />
				<!-- 
					modelValue
					update:modelValue
				 -->
				<!-- <LabelInput
					:model-value="username"
					@update:model-value="value => (username = value)"
				></LabelInput> -->
				<LabelInput
					v-model="username"
					label="이름"
					class="parent-class"
					style="color: red"
					id="parent-id"
				></LabelInput>
			</div>
		</main>
	</div>
</template>

<script>
import { reactive, ref } from 'vue';
import PostItem from './PostItem.vue';
import PostCreate from '@/components/PostCreate.vue';
import LabelInput from '@/components/LabelInput.vue';

export default {
	components: {
		PostItem,
		PostCreate,
		LabelInput,
	},
	setup() {
		const post = reactive({
			title: '제목2',
			content: '내용2',
		});

		const posts = reactive([
			{ id: 1, title: '제목1', contents: '내용1', isLike: true, type: 'news' },
			{ id: 2, title: '제목2', contents: '내용2', isLike: true, type: 'news' },
			{ id: 3, title: '제목3', contents: '내용3', isLike: true, type: 'news' },
			{
				id: 4,
				title: '제목4',
				contents: '내용4',
				isLike: true,
				type: 'news',
			},
			{
				id: 5,
				title: '제목5',
				contents: '내용5',
				isLike: false,
				type: 'notice',
			},
			{
				id: 6,
				title: '제목6',
				contents: '내용6',
				isLike: false,
				type: 'notice',
			},
		]);

		const createPost = newPost => {
			console.log('createPost', newPost);
			posts.push(newPost);
		};

		const username = ref('');
		const firstname = ref('');
		const lastname = ref('');

		return { post, posts, createPost, username, firstname, lastname };
	},
};
</script>

<style lang="scss" scoped></style>
