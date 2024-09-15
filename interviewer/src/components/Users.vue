<template>
  <div>
    <h2>User List</h2>
    <ul>
      <li v-for="user in users" :key="user.Id">
        {{ user.Username }} 
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const users = ref([]);

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:8080/api/users');
    console.log("RESPONSE:", response, "\n")
    users.value = response.data.users;
  } catch (error) {
    console.error('Failed to fetch users', error);
  }
});
</script>

<style>
/* Add your styles here */
</style>