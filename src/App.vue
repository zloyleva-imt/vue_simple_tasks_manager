<template>
  <div id="app">
	  <b-container class="bv-example-row">
		<b-row>
			<b-col cols="12">
				<h1>{{ msg }}</h1>
			</b-col>
			<b-col cols="12">
				<CreateTaskForm 
					@addNewTaskEvent="addNewTask"
				></CreateTaskForm>
			</b-col>

			<b-col cols="12 mt-4">
				<b-tabs content-class="mt-3">
					<b-tab title="All" active @click="selectTab('all')"></b-tab>
					<b-tab title="Done" @click="selectTab('done')"></b-tab>
					<b-tab title="Not done" @click="selectTab('not-done')"></b-tab>
				</b-tabs>
			</b-col>

			<b-col cols="12">
				<TasksList 
					:tasks="filteredTasks"
					@clickToChangetaskStatusEvent="clickToChangetaskStatus"
				></TasksList>
			</b-col>
		</b-row>
	</b-container>
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
		tab:"all",
	}
  },
  computed:{
	filteredTasks(){
		return this.tasks.filter(el => {
			switch (this.tab){
				case 'done':
					return el.isDone;
				case 'not-done':
					return !el.isDone;
				default:
					return true;
			}
		});
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
	},
	selectTab(tab){
		console.log("selectTab", tab);
		this.tab = tab;
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
