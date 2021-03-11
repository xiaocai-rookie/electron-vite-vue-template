<template>
  <Helo :msg="`Electron ${ state.version }`" />
  <Helo :msg="`Vue3 + Vite2`" />
  <div>
    <el-button style="width: 60%;" @click="increment">点我</el-button>
  </div>
  <p>统计: {{state.count}}</p>
  <p>双倍统计: {{state.double}}</p>
  <router-link class="success" to="/create">跳转路由</router-link>
</template>

<script>
import Helo from '../components/HelloWorld.vue';
import { reactive, computed } from 'vue';
const electronVersion = require('process').versions.electron;
export default {
  name: 'Index',
  components: {
    Helo
  },
  setup() {
    const state = reactive({
      count: 0,
      double: computed(() => state.count * 2),
      version: electronVersion
    })

    function increment() {
      state.count++
    }

    return {
      state,
      increment,
    }
  },
}
</script>

<style lang="scss" scoped>
.logo-box {
  width: 20%;
  margin-left: 130px;
}
.success {
  background: #00c13c;
  border: none;
  border-radius: 10px;
  padding: 10px 80px;
  color: #fff;
  text-decoration: none;
}
</style>

