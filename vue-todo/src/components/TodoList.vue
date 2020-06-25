<template>
  <div>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem.item">
        <span :class="{chkComplete: todoItem.completed}" @click="toggleComplete(todoItem, index)">##</span>
        <span :class="{textComplete: todoItem.completed}">{{ todoItem.item }}</span>
        <button @click="removeTodo(todoItem, index)">delete</button>
      </li>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: [ 'propsdata' ],
  methods: {
    removeTodo: function(todoItem, index) {
      this.$emit('removeItem', todoItem, index);
    },
    toggleComplete: function(todoItem, index) {
      todoItem.completed = !todoItem.completed;
      // 로컬 스토리지의 데이터를 갱신
      localStorage.removeItem(todoItem.item, index);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  },
}
</script>

<style>
  .chkComplete{color:#f00}
  .textComplete{text-decoration:line-through}

  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
    opacity: 0;
    transform: translateY(30px);
  }
</style>