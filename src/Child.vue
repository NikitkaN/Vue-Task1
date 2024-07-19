<template>
  <div>
    <h2>Дочерний компонент</h2>
    <input v-model="localMessage" @input="updateParentMessage" />
    <button @click="toggleList">Показать/Скрыть список</button>
    <ul v-if="showList">
      <li v-for="(item, index) in localItems" :key="index">
        <input v-model="localItems[index]" @input="updateParentItems" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Child',
  props: {
    message: String,
    items: Array
  },
  data() {
    return {
      localMessage: this.message,
      localItems: [...this.items],
      showList: true
    };
  },
  methods: {
    updateParentMessage() {
      this.$emit('update-message', this.localMessage);
    },
    updateParentItems() {
      this.$emit('update-items', this.localItems);
    },
    toggleList() {
      this.showList = !this.showList;
    }
  },
  watch: {
    message(newMessage) {
      this.localMessage = newMessage;
    },
    items(newItems) {
      this.localItems = [...newItems];
    }
  }
};
</script>
