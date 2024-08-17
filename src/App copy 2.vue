<script setup>
import { ref, onMounted } from "vue";

const name = ref("Jibu");
const status = ref("active");
const tasks = ref(["task one", "task two", "task three"]);
const newTask = ref("");

const toggleStatus = () => {
  if (status.value === "inactive") {
    status.value = "true";
  } else if (status === "active") {
    status.value = "false";
  } else {
    status.value = "yes";
  }
};

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const respond = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await respond.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log("error of fetching data");
  }
});
</script>

<template>
  <h1>Hell World</h1>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
  <p v-else="status">USer is Inactive</p>
  <p v-if="status2 === 'active'">User is activated</p>
  <p v-else-if="status2 == 'Inactive'">User is not activated</p>
  <p v-else>No User</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Tasks</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <a v-bind:href="link">click for Google</a>

  <button @click="toggleStatus">change Status</button>
</template>

<style scoped>
h1 {
  color: red;
}
</style>
