<template>
  <div class="container py-4">
    {{ msg }}
    <br>
    {{  message }}
    <input type="text" v-model="message">
    <button @click="sayHello">click</button>
    <PostItem type="news" title="제목" contents="내용" :is-like="true"></PostItem>
    <PostItem type="news" title="제목" contents="내용" :is-like="true"></PostItem>
    <PostItem type="news" title="제목" contents="내용" :is-like="true"></PostItem>
    <hr>
    <TemplateRefsChild ref="child"></TemplateRefsChild>
    <template v-if="child">{{  child.message  }}</template>
    <hr>
    <MyButton class="parent-class"></MyButton>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import PostItem from '@/components/setup/PostItem.vue';
import TemplateRefsChild from '@/components/setup/TemplateRefsChild.vue';
import MyButton from '@/components/setup/MyButton.vue';
import axios from 'axios';

const msg = 'Hello World!';
const sayHello = () => {
  alert('Hello world!');
};
const message = ref('');
const child = ref(null);

defineExpose({
  msg
})
const response = await axios('https://jsonplaceholder.typicode.com/posts');
console.log(response);
</script>

<style lang="scss" scoped>

</style>