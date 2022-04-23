<template>
  <div class="inputBox shadow">
    <input
      type="text"
      v-model="newTodoItem"
      placeholder="할 일을 적어주세요"
      v-on:keyup.enter="addTodo"
    />
    <span class="addContainer" @click="addTodo">+</span>

    <todo-modal v-if="showModal" @close="showModal = false"></todo-modal>
  </div>
</template>
<script>
import TodoModal from "./TodoModal.vue";

export default {
  components: { TodoModal },
  data() {
    return {
      newTodoItem: "",
      showModal: false,
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        let value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      } else {
        this.showModal = true;
      }
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
};
</script>
<style scoped>
.addContainer {
  cursor: pointer;
}
</style>
