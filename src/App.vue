<template>
  <div id="app">
    <button @click="showToast1">弹出Toast - 标准</button>
    <button @click="showToast2">弹出Toast - 快速</button>
    <button @click="showToast3">弹出Toast - 通过第三方调用</button>
    <toast ref="toast"></toast>
  </div>
</template>

<script>
  import Toast from './Toast.vue';
  import Utils from './Utils';
export default {
  name: 'app',
  components: {
    [Toast.name]: Toast
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    showToast1: function() {
      this.$refs.toast.show('Hello, World');
    },
    showToast2: function() {
      this.$refs.toast.show('昙花一现, 很快消失', 1000);
    },
    showToast3: function() {
      // 通过Utils中心调用注册的toast
      Utils.invoke('toast', '哈哈, 从Commonjs中弹出了toast', 2000);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
