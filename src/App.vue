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
      alert(this.currentTask);
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
                <label for="inputTodo" class="form-label fw-bold"
                  >Input To Do</label
                >
                <input
                  autocomplete="off"
                  placeholder="input your to do"
                  type="text"
                  class="form-control"
                  id="inputTodo"
                  v-model="currentTask"
                  @keyup.enter="submitTodo"
                />
              </div>
              <button type="submit" class="btn btn-primary">save</button>
            </form>
          </div>
          <div class="col-12 mt-5">
            {{ currentTask }}
            <div class="mt-4">
              <div class="card my-2" v-for="(toDo, index) in data" :key="index">
                <div class="card-body">
                  {{ toDo }}
                </div>
                <button @click="removeTodo(index)" class="btn btn-dark">Remove</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

