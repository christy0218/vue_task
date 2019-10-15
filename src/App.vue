 <template>
	<div id="app">
		<h1>Todo Task</h1>
		<main class="flexbox">
			<!-- To Do Column -->
			<TodoBoard id="to_do" :all="todos">
				<div class="column-title">To Do</div>
				<div class="task-no">{{ taskToDo.length }}</div>
				<TodoCard :id="todo.id" draggable="true" v-for="todo in taskToDo" :key="todo.id">
					<div class="title">{{ todo.title }}</div>
					<div class="desp">{{ todo.desp }}</div>
				</TodoCard>
			</TodoBoard>

			<!-- In Progress Column -->
			<TodoBoard id="in_progress" :all="todos">
				<div class="column-title">In Progress</div>
				<div class="task-no">{{ taskInProgress.length }}</div>
				<TodoCard :id="todo.id" draggable="true" v-for="todo in taskInProgress" :key="todo.id">
					<div class="title">{{ todo.title }}</div>
					<div class="desp">{{ todo.desp }}</div>
				</TodoCard>
			</TodoBoard>

			<!-- Done Column -->
			<TodoBoard id="done" :all="todos">
				<div class="column-title">Done</div>
				<div class="task-no">{{ taskDone.length }}</div>
				<TodoCard :id="todo.id" draggable="true" v-for="todo in taskDone" :key="todo.id">
					<div class="title">{{ todo.title }}</div>
					<div class="desp">{{ todo.desp }}</div>
				</TodoCard>
			</TodoBoard>
		</main>
	</div>
</template>

<script>
import TodoBoard from './components/TodoBoard.vue'
import TodoCard from './components/TodoCard.vue'

export default {
	name: 'app',
	components: {
		// Add a reference to the component
		TodoCard,
		TodoBoard
	},
	// Create Data
	data() {
		return {
			// Create an array of Todos
			todos: [
				{
					id: 0,
					title: 'Task A',
					desp: 'This is task A.',
					progress: 'to_do',
				},
				{
					id: 1,
					title: 'Task B',
					desp: 'This is task B.',
					progress: 'to_do',
				},
				{
					id: 2,
					title: 'Task C',
					desp: 'This is task C.',
					progress: 'in_progress',
				},
				{
					id: 3,
					title: 'Task D',
					desp: 'This is task D.',
					progress: 'in_progress',
				},
				{
					id: 4,
					title: 'Task E',
					desp: 'This is task E.',
					progress: 'in_progress',
				},
				{
					id: 5,
					title: 'Task F',
					desp: 'This is task F.',
					progress: 'done',
				},
			]
		}
	},
	computed: {
		// Get the To Do Tasks
		taskToDo: function () {
			return this.todos.filter(function (todo) {
				return todo.progress === 'to_do';
			})
		},
		// Get the In Progress Tasks
		taskInProgress: function () {
			return this.todos.filter(function (todo) {
				return todo.progress === 'in_progress';
			})
		},
		// Get the Done Tasks
		taskDone: function () {
			return this.todos.filter(function (todo) {
				return todo.progress === 'done';
			})
		}
	}
}
</script>

<style lang="scss">

#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

// Page Title
h1 {
	margin-top: 40px;
}

// Todo list
.flexbox {
	display: flex;
	justify-content: space-around;
	width: 100%;
	max-width: 70%;
	overflow: hidden;
	margin: 0 auto;
	padding: 15px;

	// Task List Board
	.board {
		display: flex;
		flex-direction: column;
		position: relative;
		width: 20%;
		text-align: left;
		margin: 40px 20px;
		padding: 40px;
		border-radius: 20px;
		box-shadow: 10px 10px 50px -20px rgba(0,0,0,0.2);

		.column-title {
			width: 80%;
			color: mediumaquamarine;
			font-weight: 600;
			font-size: 24px;
		}

		.task-no {
			position: absolute;
			top: 40px;
			right: 40px;
			font-weight: 600;
			font-size: 24px;
		}
	}

	// Task Card
	.card {
		cursor: pointer;
		margin: 10px 0;
		padding: 20px;
		border: 1px solid #9f9f9f;
		border-radius: 20px;
		.title {
				font-weight: 600;
				font-size: 20px;
		}
	}
}
</style>
