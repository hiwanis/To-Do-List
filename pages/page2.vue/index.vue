<template>
  <div class="container">
    <div class="text-center text-info mt-3">
      <h3>To-Do List</h3>
    </div>
    <div class="d-flex flex-row justify-content-center">
      <div class="col-md-8 mt-5">
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li
                class="list-group-item"
                v-for="(todo, index) in listItems"
                :key="todo"
              >
                {{ todo }}

                <button
                  class="btn btn-danger float-right"
                  @click="removeTodo(index)"
                >
                  <i class="fa fa-trash" aria-hidden="true"></i>
                </button>
              </li>
            </ul>

            <form @submit.prevent="sub">
              <div class="form-group mt-5">
                <input
                  type="text"
                  placeholder="Add a To-Do"
                  class="form-control"
                  v-model="todo"
                />
                <button class="btn btn-outline-info mt-3">Add To-Do</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: "",
      listItems: ["Exercises", "Stretches", "Coding", "Tutorials"],
    };
  },
  methods: {
    // The @submit.prevent function assigned as sub() triggers the form to be submitted
    sub() {
      if (!this.listItems.includes(this.todo.trim())) {
        this.listItems.push(this.todo);
        this.todo = "";
      } else {
        alert("error");
      }
    },
    // The remove function will remove the array, when button pressed
    removeTodo(index) {
      this.$delete(this.listItems, index);
    },
  },
};
</script>