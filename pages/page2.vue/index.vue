<template>
  <div class="container">
    <div class="text-center text-info mt-3">
      <h3>To-Do List</h3>
    </div>
    <div class="d-flex flex-row justify-content-center">
      <div class="col-md-8 mt-5">
        <div class="card">
          <div class="card-body">
            <input type="text" v-model="item" @keypress.enter="add" />
            {{ item }}
            <ul class="list-group">
              <li v-for="(item, index) in items" :key="index">
                {{ item }}
                <button @click="remove(index)">-</button>
              </li>
            </ul>
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
      items: [],
      item: "",
    };
  },
  methods: {
    add(item) {
      this.items.push(item);
    },
    remove(index) {
      this.items.splice(index, 1);
    },
  },
};
</script>