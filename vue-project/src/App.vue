<script>
export default{
  data(){
    return{
      item: '',
      todoList: [],
    }
  },
  methods: {
    addTodo(){
      this.todoList.push(this.item);
      this.item = "";
    },
  removeTodo (index) {
    this.todoList.splice(index, 1);
    },
},
}
</script>

<template>
 <div class="app">
 <div class="content">
    <h1>Список дел</h1>
    <p>Тут ты можешь записать все свои дела!</p>
    <hr>
  </div>
  <div id="app-todolist" class="what-to-do">
    <input type="text" placeholder="Напиши сюда задачу" v-model="item">
    <button v-if="item==''" disabled title="Введите текст">+</button>
    <button v-else @click="addTodo()" title="Добавить новую задачу">+</button>
  </div>
  <div id="main-content" class="List">
    <ul>
      
		<li v-for="(todo, index) in todoList" :key="index" class="todo-item">
      {{ todo }} 
      <input type="checkbox" class="check" title="Выполнено"/>
      <button @click="removeTodo(index)"  title="Удалить задачу" class="del">x</button>
    </li>
    </ul>
  </div> 
</div>    
</template>

<style scoped>
.app{
  background-color: #000;
  border-radius: 30px;
  text-align: center;
  margin:auto;
  margin-top: 50px;
  margin-bottom: 50px;
  color: #FFF;
  box-sizing: border-box;
}
.content h1{
  text-transform: uppercase;
  padding-top: 10px;
  padding-bottom: 10px;
  font-size: 40px;
}
.content p{
  padding-bottom: 10px;
}
.what-to-do input{
  width: 80%;
  height: 40px;
  font-size: 20px;
  margin-top: 30px;
  border: 0;
  background-color: transparent;
  border-bottom: 1px solid gray;
  padding: 2px;
  color:#FFF;
  text-transform: uppercase ;
  text-align: center;
}
.what-to-do input:focus{
  outline: none;
}
.what-to-do button {
  width: 50px;
  height: 50px;
  text-align: center;
  font-size: 24px;
  color: #FFF;
  border: none;
  border-radius: 10px;
  background-color: transparent;
  margin-top: 20px;
  margin-bottom: 20px;
  cursor: pointer;
}
.what-to-do button:hover {
  background-color: #ffffff32;
}
.List li{
  font-size: 20px;
  margin-left: 40px;
  text-align: left;
  word-wrap: break-word;
  border: 0;
  background-color: transparent;
  padding: 2px;
  color:#FFF;
  list-style-type: none;
}
.check {
	height: 18px;
	width: 18px;
	cursor: pointer;
}
.del {
  width: 30px;
  text-align: center;
  font-size: 20px;
  color: #FFF;
  border: none;
  border-radius: 10px;
  background-color: transparent;
  margin-top: 20px;
  margin-bottom: 20px;
  cursor: pointer;
}
.del:hover {
  background-color: #5f6368;
}

</style>
