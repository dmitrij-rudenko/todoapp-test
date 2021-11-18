<template>
	<v-list-item-group>
		<v-list-item v-for="todo in todos" :key="todo.id" class="todo-item">
			<v-list-item-content class="todo-item__content">{{ todo.text }}</v-list-item-content>
			<v-list-item-icon>
				<v-btn @click="removeTodo(todo)">
					<v-icon v-text="'mdi-delete'"></v-icon>
				</v-btn>
			</v-list-item-icon>
		</v-list-item>
	</v-list-item-group>
</template>

<script>
export default {
	computed: {
		todos() {
			return this.$store.state.todos.list
		},
	},
	methods: {
		removeTodo(todo) {
			this.$store.commit('todos/remove', todo)
		},
	},
}
</script>

<style lang="scss">
.todo-item {
	border-bottom: 1px solid #000;

	&:last-child {
		border-bottom: none;
	}

  &__content {
    white-space: pre-wrap;
  }
}
</style>
