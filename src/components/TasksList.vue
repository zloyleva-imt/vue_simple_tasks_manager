<template>
	<ul class="list-unstyled mt-4">
		<li v-for="task in tasks" 
			:key="task.id" 
			:class="{'is-done':task.isDone}"
			@click="clickToChangetaskStatus(task)"
		>
			<b-card class="my-2" :title="task.title"></b-card>
		</li>
	</ul>
</template>

<script>
export default {
	name: 'TasksList',
	props: ['tasks'],
	methods:{
		clickToChangetaskStatus(task){
			this.$emit("clickToChangetaskStatusEvent", task)
		}
	}
}
</script>
