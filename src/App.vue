<!-- ParentComponent.vue -->
<template>
  <div class="container">
    <div class="cardbox">
      <NavBar />
      <div class="todo-list">
        <TodoCard
          v-for="task in task"
          :key="task.id"
          :id="task.id"
          :name="task.name"
          :date="task.date"
          v-model:isDone="task.isDone"
          @delete="delTodo"
        />
      </div>
      <form @submit="appendTask" v-show="showAdd" class="addtask">
        <i @click="toggleAdd" class="close fa-solid fa-x"></i>
        <input v-model="addTask.name" type="text" class="name" />
        <input v-model="addTask.date" type="date" class="date" />
        <div class="isUrgent">
          <input v-model="addTask.isUrgent" type="checkbox" name="urgent" />
          <label for="urgent"> Important </label>
        </div>
        <button class="btn" type="submit">Add</button>
      </form>
      <i @click="toggleAdd" class="add fa-solid fa-plus"></i>
    </div>
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import TodoCard from "./components/TodoCard.vue";

export default {
  name: "App",
  components: {
    NavBar,
    TodoCard,
  },
  data() {
    return {
      showAdd: false,
      addTask: [
        {
          id: Math.floor(Math.random() * 1947),
          name: "",
          date: "",
          isUrgent: false,
          isDone: false,
        },
      ],
      task: [
        {
          id: 1,
          name: "Go to a doctor",
          date: "October 22",
          isUrgent: true,
          isDone: false,
        },
        {
          id: 2,
          name: "Have a dinner date",
          date: "October 23",
          isUrgent: false,
          isDone: true,
        },
        {
          id: 3,
          name: "Buy groceries",
          date: "October 24",
          isUrgent: true,
          isDOne: false,
        },
      ],
    };
  },
  methods: {
    delTodo(id) {
      this.task = this.task.filter((task) => task.id !== id);
    },
    toggleAdd() {
      this.showAdd = !this.showAdd;
    },
    appendTask(e) {
      e.preventDefault();
      this.task = [...this.task, this.addTask];

      this.addTask = [
        {
          id: Math.floor(Math.random() * 1947),
          name: "",
          date: "",
          isUrgent: false,
          isDone: false,
        },
      ];
    },
  },
};
</script>

<style scoped>
.container {
  background-color: #212121;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.cardbox {
  position: relative;
  width: 300px;
  height: 500px;
  padding: 10px;
  border-radius: 30px;
  background: #212121;
  box-shadow: 15px 15px 30px rgb(25, 25, 25), -15px -15px 30px rgb(60, 60, 60);
}

.todo-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

.add {
  background-color: #333;
  color: #fff;
  position: absolute;
  bottom: 9%;
  right: 12%;
  padding: 1rem;
  border-radius: 14px;
  cursor: pointer;
  font-size: 1.2rem;
}

.addtask {
  background-color: #333;
  color: hsl(0, 0%, 100%);
  width: 300px;
  height: 500px;
  position: absolute;
  bottom: 1%;
  left: 1%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 5px;
  padding: 1rem;
  border-radius: 14px;
  z-index: 100;
  box-shadow: 15px 15px 30px rgb(25, 25, 25), -15px -15px 30px rgb(60, 60, 60);
}

.name,
.date,
.isUrgent,
.btn {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
}

.name,
.date {
  background-color: #444; /* Darker background color for inputs */
  color: #fff; /* Text color */
}

.isUrgent {
  display: flex;
  align-items: center;
}

.isUrgent input[type="checkbox"] {
  margin-right: 5px;
}

.btn {
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
}

.btn:hover {
  background-color: #0056b3;
}

.close {
  position: absolute;
  top: 8%;
  right: 10%;
  font-size: 1.2 rem;
  cursor: pointer;
}

.close:hover {
  transform: rotate(90deg);
}
</style>
