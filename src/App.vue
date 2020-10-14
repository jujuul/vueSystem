<!--
 * @Author: your name
 * @Date: 2020-10-14 12:29:54
 * @LastEditTime: 2020-10-14 15:16:11
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \vueSystem\vue-demo\src\App.vue
-->
<template>
  <div id="app">
    <input v-model="message" />
    <input :value="message" @input="handelChange" />
    {{ message }}
    <todo-list>
      <todo-item
        @delete="handelDelete"
        v-for="item in list"
        :title="item.title"
        :del="item.del"
        :key="item.title"
      >
        <template v-slot:pre-icon="{ value }">
          <span>前置图标{{ value }}</span>
        </template>
        <template v-slot:suf-icon> </template>
      </todo-item>
    </todo-list>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoItem,
    TodoList,
  },
  data() {
    return {
      message: "hello world",
      list: [
        {
          title: "课程1",
          del: false,
        },
        {
          title: "课程2",
          del: true,
        },
      ],
    };
  },
  methods: {
    handelDelete(val) {
      console.log("handelDelete", val);
    },
    handelChange(e) {
      this.message = e.target.value;
    },
  },
};
</script>