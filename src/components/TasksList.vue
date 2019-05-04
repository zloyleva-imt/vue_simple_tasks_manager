<template>
	<ul>
		<li v-for="task in tasks" 
			:key="task.id" 
			:class="{'is-done':task.isDone}"
			@click="clickToChangetaskStatus(task)"
		>
			{{ task.title }}
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
