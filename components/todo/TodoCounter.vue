<template>
	<v-dialog v-model="show" width="500">
		<v-card>
			<v-card-text class="pa-5">
				Общее количество задач: {{ itemsCount }}
			</v-card-text>

			<v-divider></v-divider>

			<v-card-actions>
				<v-spacer></v-spacer>
				<v-btn color="red" text @click="$emit('close')">Закрыть</v-btn>
			</v-card-actions>
		</v-card>
	</v-dialog>
</template>

<script>
export default {
	data: () => ({
		show: true,
	}),
	computed: {
		itemsCount() {
			return this.$store.state.todos.list.length
		},
	},
}
</script>