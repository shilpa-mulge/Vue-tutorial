<script>
export default {
  data() {
    return {
      task: "",
      editedTask: null,
      statuses: ["To-do", "In-progress", "Finished"],
      tasks: [
        {
          name: "read book",
          status: "to-do",
        },
        {
          name: "play football",
          status: "in-progress",
        },
      ],
    };
  },
  methods: {
    submitTask() {
      if (this.task.length === 0) return;
      if (this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    changeStatus(index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.statuses[newIndex];
    },
  },
};
</script>

<template>
  <div class="container">
    <h2 class="mt-5 text-center">My todo App</h2>
  </div>
  <div class="d-flex">
    <input
      v-model="task"
      type="text"
      placeholder="enter task"
      class="form-control"
    />
    <button @click="submitTask" class="btn btn-warning rounded-0">
      submit
    </button>
  </div>
  <table class="table table-dark mt-5 w-100">
    <thead>
      <tr>
        <th scope="col">Task</th>
        <th scope="col">Status</th>
        <th scope="col">#</th>
        <th scope="col">#</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(task, index) in tasks" :key="index">
        <td>
          <span :class="{ finished: task.status === 'Finished' }">{{
            task.name
          }}</span>
        </td>
        <td style="width: 120px">
          <span
            @click="changeStatus(index)"
            class="pointer"
            :class="{
              'text-danger': task.status === 'To-do',
              'text-warning': task.status === 'In-progress',
              'text-success': task.status === 'Finished',
            }"
            >{{ task.status }}</span
          >
        </td>
        <td>
          <div class="text-center" @click="editTask(index)">
            <span class="fa fa-pen"></span>
          </div>
        </td>
        <td>
          <div class="text-center" @click="deleteTask(index)">
            <span class="fa fa-trash"></span>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style>
.pointer {
  cursor: pointer;
}
.finished {
  text-decoration: line-through;
}
</style>
