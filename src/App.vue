<template>
  <div id="app">
    <h1>{{ msg }}</h1>

	<CreateTaskForm 
		@addNewTaskEvent="addNewTask"
	></CreateTaskForm>

	<TasksList 
		:tasks="tasks"
		@clickToChangetaskStatusEvent="clickToChangetaskStatus"
	></TasksList>
  </div>
</template>

<script>
import CreateTaskForm from './components/CreateTaskForm.vue'
import TasksList from './components/TasksList';

export default {
  name: 'app',
  components: {
    CreateTaskForm, TasksList
  },
  data(){
	return{
		msg:"Task list",
		tasks: [
			{id:1, title: "Get up", isDone: true},
			{id:2, title: "Clean teeth", isDone: false},
			{id:3, title: "Go out", isDone: false},
		],
	}
  },
  methods:{
	addNewTask(task_title){
		console.log(task_title);
		this.tasks.push({
				id:this.tasks.length +1, title:task_title, isDone: false
			});
		this.task_title = "";
	},
	clickToChangetaskStatus(task){
		task.isDone = !task.isDone;
	}
  }
}
</script>

<style>
	h1{
		color:brown;
	}
	.is-done{
		text-decoration: line-through;
	}
</style>
