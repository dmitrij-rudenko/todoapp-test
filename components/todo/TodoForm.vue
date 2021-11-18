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
					@click.prevent="counterDialog = true"
				>
					Открыть счетчик
				</v-btn>
			</div>
		</v-form>
		<v-dialog v-model="counterDialog" class="counter-dialog" width="500">
			<v-card>
				<v-card-text class="pa-5">
					Общее количество задач: {{ itemsCount }}
				</v-card-text>

				<v-divider></v-divider>

				<v-card-actions>
					<v-spacer></v-spacer>
					<v-btn color="red" text @click="counterDialog = false">Закрыть</v-btn>
				</v-card-actions>
			</v-card>
		</v-dialog>
	</div>
</template>

<script>
export default {
	data: () => ({
		newTodoText: '',
		counterDialog: true,
	}),

	computed: {
		itemsCount() {
			return this.$store.state.todos.list.length
		},
	},

	methods: {
		addTodo() {
			if (!this.newTodoText.trim().length) return

			this.$store.commit('todos/add', this.newTodoText)
			this.newTodoText = ''
		},
	},
}
</script>