<template>
	<div>
		<form @submit="addTodo">
			<input type="text" v-model="name" name="name" placeholder="Dodaj grad...">
			<input type="submit" value="Submit" class="btn">
		</form>
	</div>
</template>

<script>
import uuid from 'uuid';
export default {
	name: "AddTodo",
	data() {
		return {
			name: ''
		}
	},
	methods: {
		addTodo(e) {
			e.preventDefault();
			const newTodo = {
				id: uuid.v4(),
				name: this.name,
				completed: false
			}
			// Send up to parent
			this.$emit('add-todo', newTodo);
			this.title = '';
		}
	}
}
</script>

<style scoped>
	form {
		display: flex;
	}
	input[type="text"] {
		flex: 10;
		padding: 5px;
	}
	input[type="submit"] {
		flex: 2;
	}
</style>