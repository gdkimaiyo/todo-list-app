<template>
  <div id="todo-task-form" class="sub-content-element">
    <h3>Add Todo Task</h3>
    <form @submit.prevent="handleSubmitTask">
      <span>
        <input
          type="text"
          class="search-form"
          v-model="todoTask.task"
          @focus="clearStatus"
          @keypress="clearStatus"
          placeholder="Add New Task"
        />
      </span>
      <span>
        <button type="button" name="button" class="button btn-info" @click="handleSubmitTask">Add</button>
      </span>
      <span v-if="error && submitting" class="error-message">Please fill out a task.</span>
      <span v-if="success" class="success-message">Success. Task added!</span>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTaskForm",

  data() {
    return {
      error: false,
      success: false,
      submitting: false,

      todoTask: {
        task: ""
      }
    };
  },

  props: {},

  components: {},

  computed: {},

  methods: {
    handleSubmitTask(ev) {
      ev.preventDefault();
      (this.submitting = true), this.clearStatus();

      if (this.todoTask.task == "") {
        this.error = true;
        return;
      }

      this.$emit("add:task", this.todoTask);
      this.todoTask = {
        task: ""
      };

      this.error = false;
      this.success = true;
    },
    clearStatus() {
      this.success = false;
      this.error = false;
    }
  }
};
</script>
