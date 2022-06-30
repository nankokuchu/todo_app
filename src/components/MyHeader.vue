<template>
  <div class="todo-header" @keydown.enter="add">
    <input type="text" placeholder="TODOを入力してください"/>
  </div>
</template>

<script>
import {nanoid} from 'nanoid'

export default {
  name: "MyHeader",
  props: ['addTodo'],
  methods: {
    add(e) {
      //データをチェックする
      if (!e.target.value.trim()) return alert('コンテンツを入力してください')

      //ユーザが入力した内容をtodoのオブジェクトにする
      const todoObj = {id: nanoid(), title: e.target.value, done: false}

      //App组件里传数据
      this.addTodo(todoObj)

      //清空输入
      e.target.value = ''
    }
  }
}
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}
</style>