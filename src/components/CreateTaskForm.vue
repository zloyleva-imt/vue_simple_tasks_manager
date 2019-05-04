<template>
	
	<div>
		<transition name="slide-fade">
			<b-form @submit.prevent="addNewTask" v-if="isShowForm">
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
		</transition>
		<transition name="slide-fade">
			<div v-if="!isShowForm">
				<b-button variant="danger" @click="toggleDisplayForm">Show form</b-button>
			</div>
		</transition>
	</div>
	
</template>

<script>
export default {
	name: 'CreateTaskForm',
	data(){
		return {
			task_title:"",
			isShowForm: false,
		}
	},
	methods:{
		addNewTask(){
			this.$emit('addNewTaskEvent', this.task_title);
			this.task_title = "";
			this.toggleDisplayForm();
		},
		toggleDisplayForm(){
			this.isShowForm = !this.isShowForm;
		}
	}
}
</script>

<style>
	.slide-fade-enter-active {
		transition: all .3s ease;
	}
	.slide-fade-leave-active {
		transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
	}
	.slide-fade-enter, .slide-fade-leave-to{
		transform: translateX(350px);
		opacity: 0;
	}
</style>
