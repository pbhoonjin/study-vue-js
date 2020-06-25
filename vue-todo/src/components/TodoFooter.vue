<template>
  <div>
    <button @click="clearTodo">Clear All</button>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo: function() {
      this.$emit('clearAll');
    }
  }
}
</script>

<style scoped>
  
</style>