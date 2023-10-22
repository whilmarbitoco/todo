<template>
  <div
    :style="{ borderLeft: isDone ? '2px solid green' : '2px solid red' }"
    class="card"
    @dblclick="toggleDone"
  >
    <div class="content">
      <h2>{{ name }}</h2>
      <div class="info">
        <p class="date">{{ date }}</p>
        <p class="urgency"><i class="color fa-solid fa-circle"></i>Important</p>
      </div>
    </div>
    <div class="delete">
      <i @click="delTodo(this.id)" class="fa-solid fa-trash"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoCard",
  props: {
    id: Number,
    name: String,
    date: String,
    isDone: Boolean,
    isUrgent: Boolean,
  },
  methods: {
    toggleDone() {
      this.$emit("update:isDone", !this.isDone);
    },
    delTodo(id) {
      this.$emit("delete", id);
    },
  },
};
</script>

<style scoped>
.card {
  width: 100%;
  max-width: 290px;
  height: 80px;
  background: #353535;
  color: #fff;
  display: flex;
  justify-content: space-between;
  padding: 15px;
  cursor: pointer;
}

h2 {
  font-size: 16px;
  font-weight: bold;
}

.date,
.urgency {
  font-size: 12px;
  font-weight: lighter;
  margin: 10px;
}

.info {
  display: flex;
}

.color {
  font-size: 8px;
  color: red;
  margin-right: 5px;
}

.delete {
  color: red;
  font-size: 17px;
  cursor: pointer;
}
</style>
