<template>
  <div class="container py-4">
    <input ref="input" type="text">
    <p> {{ input }} </p>
    <p v-if="input">{{ input.value }}, {{ $refs.input.value }}, {{ $refs.input ===  input }}</p>
    <hr>
    <ul>
      <!-- <li v-for="fruit in fruits" :key="fruit" ref="itemRefs">{{ fruit  }}</li> -->
      <li v-for="fruit in fruits" :key="fruit" :ref="el => itemRefs.push(el.textContent)">{{ fruit  }}</li>
    </ul>
    <hr>
    <TemplateRefsChild ref="child"></TemplateRefsChild>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
import TemplateRefsChild from './TemplateRefsChild.vue';

export default {
  components:{
    TemplateRefsChild
  },
  setup () {
    const input = ref(null);
    console.log("setup :", input.value);
    
    onMounted(() => {
      input.value.value = 'hello World'
      console.log("onMounted :", input.value);

      itemRefs.value.forEach(item => {
        // console.log(item.textContent);
        console.log(item);
      });


      console.log(child.value.message);
      child.value.sayHello()
    });


    const fruits = ref(['사과', '딸기', '포도']);
    const itemRefs = ref([]);

    const child = ref();
    

    return {input, fruits, itemRefs, child}
  }
}
</script>

<style lang="scss" scoped>

</style>