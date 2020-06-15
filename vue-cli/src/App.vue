<template>
  <div>
    <app-header 
      :propsdata="str"
      @renew="renewStr"></app-header>
  </div>
  <!-- template root에는 하나의 엘리먼트 태그만 존재해야함 -->
</template>

<script>
import AppHeader from './components/AppHeader.vue'; // 가급적 .vue 확장자를 붙여줄 것
// var AppHeader = {
//   template: '<header><h1>Header</h1></header>'
// }

export default {
  data: function() {
    return {
      str: 'Header'
    }
  },
  components: {
    'app-header' : AppHeader
  },
  methods: {
    renewStr: function() {
      this.str = '안녕하세요';
    }
  }
}
</script>

<style>

</style>