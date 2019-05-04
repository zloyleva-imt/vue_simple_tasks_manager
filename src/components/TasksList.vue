<template>
	<ul class="list-unstyled mt-4">
		<transition-group name="list" tag="p">
			<li v-for="task in tasks" 
				:key="task.id" 
				:class="{'is-done':task.isDone}"
				@click="clickToChangetaskStatus(task)"
			>
				<b-card class="my-2" :title="task.title"></b-card>
			</li>
			<li v-if="showMsg" key="asdfgdfg">
				<b-card class="my-2 bg-info text-white" title="No tasks yet..."></b-card>
			</li>
		</transition-group>
	</ul>
</template>

<script>
export default {
	name: 'TasksList',
	props: ['tasks'],
	computed:{
		showMsg(){
			return !this.tasks.length;
		}
	},
	methods:{
		clickToChangetaskStatus(task){
			this.$emit("clickToChangetaskStatusEvent", task)
		}
	},
}
</script>

<style>
	.list-item {
		display: inline-block;
		margin-right: 10px;
	}
	.list-enter-active, .list-leave-active {
		transition: all 1s;
	}
	.list-enter, .list-leave-to /* .list-leave-active до версии 2.1.8 */ {
		opacity: 0;
		transform: translateY(130px);
	}
</style>
