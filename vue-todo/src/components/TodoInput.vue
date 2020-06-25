<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo">
    <button @click="addTodo"><i class="fas fa-plus"></i></button>
    <button id="show-modal" @click="showModal = true">Show Modal</button>
    <Modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">
        경고
        <button @click="showModal= false">X</button>
      </h3>
      <div slot="body">모달입니다.</div>
      <div slot="footer">copyright</div>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'
export default {
  data: function() {
    return {
      newTodoItem: "",
      showModal : false
    }
  },
  methods: {
    addTodo: function() {
      // 저장하는 로직
      if (this.newTodoItem !== '') {
        this.$emit('addTodoItem', this.newTodoItem);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput: function() {
      this.newTodoItem = '';
    }
  },
  components: {
    Modal
  }
}
</script>

<style>
  .addContainer{
    float:right
  }
</style>