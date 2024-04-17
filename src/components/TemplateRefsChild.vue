<template>
  <div>
    Child Component
    <p>{{ $parent }}</p>
    <hr>
    <ul>
      <li v-for="fruit in $parent.fruits" :key="fruit">{{ fruit }}</li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const message = ref('Hello Child!');
    const sayHello = () => {
      alert(message.value);
    };

    return {message, sayHello}
  }
}
</script>

<style lang="scss" scoped>

</style>