<template>
  <div class="content">
    <div class="sub-content">
      <add-task-form @add:task="AddTask" />

      <p>
        <list-item :tasks="tasks" @complete:task="completeTask" @delete:tasks="deleteAll" />
      </p>
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
import AddTaskForm from "./AddTaskForm.vue";

export default {
  name: "TodoList",

  components: {
    ListItem,
    AddTaskForm
  },

  props: {},

  data() {
    return {
      filterTask: "",

      tasks: [
        {
          id: 1,
          task: "Create a Todo list with vue",
          completed: true
        },
        {
          id: 2,
          task: "Create a Todo list with Vanilla JavaScript",
          completed: true
        },
        {
          id: 3,
          task: "Create a Todo list with react",
          completed: false
        },
        {
          id: 4,
          task: "Create a Todo list with angular",
          completed: false
        }
      ]
    };
  },

  methods: {
    AddTask(todoTask) {
      const lastId =
        this.tasks.length > 0 ? this.tasks[this.tasks.length - 1].id : 0;
      const id = lastId + 1;
      const completed = false;
      const newTodoTask = { ...todoTask, id, completed };

      this.tasks = [...this.tasks, newTodoTask];
    },
    completeTask(id) {
      const targetId = id - 1;
      this.tasks[targetId].completed = !this.tasks[targetId].completed;
    },
    deleteAll() {
      this.tasks = [];
    }
  }
};
</script>
