<script>
export default {
  data() {
    return {
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
    <button class="btn btn-warning rounded-0">submit</button>
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
        <td>{{ task.name }}</td>
        <td>{{ task.status }}</td>
        <td>
          <div class="text-center">
            <span class="fa fa-pen"></span>
          </div>
        </td>
        <td>
          <div class="text-center">
            <span class="fa fa-trash"></span>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped></style>
