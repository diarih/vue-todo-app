<script>
export default {
  data() {
    return {
      currentTask: "",
      data: [],
    };
  },
  methods: {
    submitTodo() {
      if (!this.currentTask.length) {
        return alert("Your Input is Empty");
      }
      this.data.push(this.currentTask);
      this.currentTask = ""
      console.log(this.data);
    },
    removeTodo(index) {
      console.log(index);
      this.data.splice(index, 1);
    },
  },
};
</script>

<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-5 m-auto">
        <div class="row">
          <div class="col-12">
            <form @submit.prevent="submitTodo">
              <div class="mb-3">
                <label for="inputTodo" class="form-label fw-bold text-light">Input To Do</label>
                <input
                  autocomplete="off"
                  placeholder="input your to do"
                  type="text"
                  class="form-control"
                  id="inputTodo"
                  v-model="currentTask"
                />
              </div>
              <button type="submit" class="btn btn-light">save</button>
            </form>
          </div>
          <div class="col-12 mt-5 text-light">
            You"re Gonna? {{ currentTask }}
            <div class="mt-4">
              <div class="card my-2" v-for="(toDo, index) in data" :key="index">
                <div class="card-body row">
                  <div class="col-10 my-auto text-dark">{{ toDo }}</div>
                  <div class="col-2 mt-auto">
                    <button @click="removeTodo(index)" class="btn btn-dark ms-auto">X</button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
body {
  background-color: #171717;
}
</style>