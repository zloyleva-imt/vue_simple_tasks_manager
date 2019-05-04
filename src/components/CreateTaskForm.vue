<template>
	<form action="" @submit.prevent="addNewTask">
		<input type="text" v-model="task_title">
		<button>Add task</button>
	</form>
</template>

<script>
export default {
	name: 'CreateTaskForm',
	data(){
		return {
			task_title:""
		}
	},
	methods:{
		addNewTask(){
			this.$emit('addNewTaskEvent', this.task_title);
			this.task_title = "";
		}
	}
}
</script>

