<script>
export default {
  data() {
    return {
      userName: "Tayyab Haseeb",
      status: "block",
      names: ["Humza", "Ahmed", "Mahnoor", "Minahil"],
    };
  },
  methods: {
    toggle() {
      console.log("Hello Tayyab");
    },
  },
};
</script>

<template>
  <h1>{{ userName }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'blocked'">User is blocked</p>
  <p v-else>user is inactive</p>
  <p>Members of family are</p>
  <ul>
    <li v-for="name in names" :key="name">{{ name }}</li>
  </ul>
  <button @click="toggle">Toggle Status</button>
</template>

<style scoped>
h1 {
  color: red;
}
</style>

<!-- SECTION 2 -->

<script setup>
import { ref } from "vue";

const userName = ref("Tayyab Haseeb");
const status = ref("active");
const names = ref(["Humza", "Ahmed", "Mahnoor", "Minahil"]);
const newNames = ref("");
function toggle() {
  if (status.value === "active") {
    status.value = "blocked";
  } else {
    status.value = "active";
  }
}

function handleSubmit() {
  if (newNames.value.trim !== "") {
    names.value.push(newNames.value);
    newNames.value = "";
  }
}
</script>

<template>
  <h1>{{ userName }}</h1>
  <form @submit.prevent="handleSubmit">
    <label for="newNames">Names</label>
    <input type="text" name="newNames" id="newNames" v-model="newNames" />
    <button type="submit">Submit</button>
  </form>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'blocked'">User is blocked</p>
  <p>Members of family are</p>
  <ul>
    <li v-for="name in names" :key="name">{{ name }}</li>
  </ul>
  <button @click="toggle">Toggle Status</button>
</template>
