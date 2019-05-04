<template>
	<b-form @submit.prevent="addNewTask">
		<b-form-group
			id="input-group-1"
			label="Task name:"
			label-for="input-1"
		>
			<b-form-input
			id="input-1"
			v-model="task_title"
			type="text"
			required
			placeholder="Enter new task"
			></b-form-input>
		</b-form-group>
		<b-button type="submit" variant="primary">Add task</b-button>
	</b-form>
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

