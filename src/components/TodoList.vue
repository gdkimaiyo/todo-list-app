<template>
  <div class="content">
    <div class="sub-content">
      <div class="sub-content-element">
        <span>
          <input
            type="text"
            class="search-form"
            id="filter"
            v-model="filterTask"
            @keyup.enter="FilterTask"
            placeholder="Search for TODO..."
          />
        </span>
      </div>

      <add-task-form @add:task="AddTask" />
      <!-- <div class="sub-content-element">
        <h3>Add TODO Task</h3>
        <span>
          <input
            type="text"
            class="search-form"
            id="filter"
            @keyup.enter="AddTask"
            placeholder="Add New Task"
          />
        </span>
        <span>
          <button type="button" name="button" class="button" @click="AddTask">
              <i class="material-icons">add</i>
          </button>
        </span>
      </div>-->

      <list-item :tasks="tasks" />
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
import AddTaskForm from "./AddTaskForm.vue";
// import BaseButton from "./BaseButton.vue";

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
          task: "Create a TODO list with vue"
        },
        {
          id: 2,
          task: "Create a TODO list with angular"
        },
        {
          id: 3,
          task: "Create a TODO list with react"
        }
      ]
    };
  },

  methods: {
    FilterTask() {
      this.$emit("filter:task", this.filterTask);
      alert("Searching isn't functional yet!..");
    },
    AddTask(todoTask) {
      console.log("AddTask triggered...");
      const lastId =
        this.tasks.length > 0 ? this.tasks[this.tasks.length - 1].id : 0;
      const id = lastId + 1;
      const newTodoTask = { ...todoTask, id };

      this.tasks = [...this.tasks, newTodoTask];
    },
    RemoveItem() {
      console.log("Remove task triggered...");
    }
  }
};
</script>
