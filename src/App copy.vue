
<script>
export default {
  data() {
    return {
      name: "Jibu Mwakilembe",
      status: "active",
      status2: "activejh",
      Tasks: ["Task one", "Task Two", "Task three"],
      link: "https://www.google.com",
    };
  },

  methods: {
    toggleStatus() {
      if (this.status === "pending") {
        this.status = "active";
      } else if (this.status === "true") {
        this.status = "Active toggle";
      } else {
        this.status = "yes";
      }
    },
  },
};
</script>

<template>
  <h1>Hell World</h1>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
  <p v-else="status">USer is Inactive</p>
  <p v-if="status2 === 'active'">User is activated</p>
  <p v-else-if="status2 == 'Inactive'">User is not activated</p>
  <p v-else>No User</p>

  <h3>Tasks</h3>
  <ul>
    <li v-for="task in Tasks" :key="task">{{ task }}</li>
  </ul>
  <a v-bind:href="link">click for Google</a>

  <button @click="toggleStatus">change Status</button>
</template>

<style scoped>
h1 {
  color: red;
}
</style>
