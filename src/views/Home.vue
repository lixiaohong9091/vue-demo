<template>
  <div class="home">
    <img alt="Vue logo"
         src="../assets/logo.png">
    <div>{{ message }}</div>
    <div>{{this.$store.state.count}}</div>
    <div v-on:click="increment">点击+{{num}}</div>
    <div><input v-model="num" /></div>
    <ul id="example-1">
      <li v-for="item in todos" :key="item">
        {{ item}}
        <el-button v-on:click="delTodos(item)">删除</el-button>
      </li>
    </ul>
    
    <div v-if="todos.length<5">
      <el-input v-model="input" placeholder="请输入内容"></el-input>
      <el-button v-on:click="addTodos">添加</el-button>
    </div>
    <div><el-button v-on:click="api">接口调用</el-button></div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import Vue from 'vue';
import home from './home.less';
export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
  data() {
    return {
      message: 'hello vue+' ,
      num: 1 ,
      todos: [ '吃饭', '睡觉', '打豆豆' ],
      input: '',

      };
  },
  methods: {
    increment() {
      this.$store.commit('increment', this.num);
      // console.log(this.$store.state.count);

    },
    addTodos() {
      if (this.input !== '') {
        this.todos.push(this.input);
      }
    },
    delTodos(params) {
     const newTds =   this.todos.filter((item) =>  item !== params  );
     this.todos = newTds;
    },
    api(params) {
     Vue.axios.get('https://srv.buysellads.com/ads/CKYD62QM.json?segment=placement:vuejsorg').then((response) => {
        // console.log(response.data);
      });
    },
  },
};

</script>
