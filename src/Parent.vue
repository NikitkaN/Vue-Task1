<template>
  <div>
    <h1>Родительский компонент</h1>
    <p>Сообщение: {{ message }}</p>
    <p>Список элементов:</p>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    <Child :message="message" :items="items" @update-message="updateMessage" @update-items="updateItems" />
  </div>
</template>

<script>
import Child from './Child.vue';

export default {
  name: 'Parent',
  components: {
    Child
  },
  data() {
    return {
      message: 'Привет из родительского компонента!',
      items: ['Элемент 1', 'Элемент 2', 'Элемент 3']
    };
  },
  methods: {
    updateMessage(newMessage) {
      this.message = newMessage;
    },
    updateItems(newItems) {
      this.items = newItems;
    }
  }
};
</script>
