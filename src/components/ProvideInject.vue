<template>
  <div class="container py-4">
    <div class="card">
      <div class="card-header">ProvideInject Component
        <p>{{ appMessage }}</p>
      </div>
      <div class="card-body">
        <button @click="count++">Click</button>
        <Child></Child>
      </div>
    </div>
  </div>
</template>

<script>
import { inject, provide, readonly, ref } from 'vue';
import Child from './Child.vue';

export default {
  components: {
    Child
  },
  setup () {
    const staticMsg = 'static message';
    const message = ref('message');
    const updateMsg = (appendMsg) => {
      message.value = message.value + appendMsg;
    }
    const count = ref(10);
    // provide('static-message', staticMsg)
    provide('message', {message: readonly(message), updateMsg})
    provide('count', count)
    const appMessage = inject('app-message');
    const msg = inject('msg');
    console.log('app msg', msg);
    return {count, appMessage}
  }
}
</script>

<style lang="scss" scoped>

</style>