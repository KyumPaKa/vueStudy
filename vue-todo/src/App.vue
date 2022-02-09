<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <!-- <TodoInput v-on:하위 컴포넌트에서 발생시킨 이벤트 이름="현재 컴포넌트의 메소드 이름"></TodoInput> -->
    <TodoInput v-on:addTodoItem="addOneItem"></TodoInput>
    <!-- <TodoList v-bind:내려보낼 프롭스 속성="현재위치의 컴포넌트 데이터 속성"></TodoList> -->
    <TodoList v-bind:propsdata="todoItems" v-on:removeItem="removeOneItem" v-on:toggleItem="toggleOneItem"></TodoList>
    <TodoFooter v-on:clearAll="clearAllItem"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

// var my_comp = {
//   template: '<div>my component</div>'
// }
// ss
// new Vue({
//   el: '',
//   components: {
//     // '컴포넌트 이름': '컴포넌트 내용'
//     'my-cmp': my_cmp
//   }
// });

export default {
    data: function() {
      return {
        todoItems: []
      }
    },
    methods: {
      addOneItem: function(todoItem) {
        var obj = {completed: false, item: todoItem};
        localStorage.setItem(todoItem, JSON.stringify(obj));
        this.todoItems.push(obj);
      },
      removeOneItem: function(todoItem, index) {
        localStorage.removeItem(todoItem.item);
        this.todoItems.splice(index, 1);
      },
      toggleOneItem: function(todoItem, index) {
        // todoItem.completed = !todoItem.completed;
        this.todoItems[index].completed = !this.todoItems[index].completed;
        // 로컬 스토리지에 데이터를 갱신
        localStorage.removeItem(todoItem.item)
        localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
      },
      clearAllItem: function() {
        localStorage.clear();
        this.todoItems = [];
      }
    },
    created: function() {
      // console.log('created');
      if(localStorage.length > 0) {
          for (var i = 0; i < localStorage.length; i++) {
              if(localStorage.key(i) !== 'loglevel:webpack-dev-server') {
                  // this.todoItems.push(localStorage.key(i));
                  this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
              }
              // console.log(localStorage.key(i));
          }
      }
  },
  components: {
    // 컴포넌트 태크명: 컴포넌트 내용
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter,
  }
}
</script>

<style>
body{
  text-align: center;
  background-color: #F6F6F6;
}
input {
  border-style: groove;
  width:200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.83);
}
</style>
