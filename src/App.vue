<script></script>

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
</template>

<style scoped></style>
