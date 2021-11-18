<template>
	<div>
		<v-form @submit.prevent="addTodo">
			<v-textarea
				v-model="newTodoText"
				class="mr-2"
				outlined
				placeholder="Описание новой задачи"
			/>
			<div class="d-flex">
				<v-btn
					type="submit"
					class="mr-2"
					color="primary"
					height="55"
					:disabled="!newTodoText"
				>
					Добавить
				</v-btn>
				<v-btn
					height="55"
					color="primary"
					@click.prevent="toggleCounter(true)"
				>
					Открыть счетчик
				</v-btn>
			</div>
		</v-form>
		<todo-counter v-if="counterDialog" @close="toggleCounter(false)"/>
	</div>
</template>

<script>
export default {
	data: () => ({
		newTodoText: '',
		counterDialog: false,
	}),

	methods: {
		addTodo() {
			if (!this.newTodoText.trim().length) return

			this.$store.commit('todos/add', this.newTodoText)
			this.newTodoText = ''
		},
		toggleCounter(isOpen) {
			this.counterDialog = isOpen
		},
	},
}
</script>