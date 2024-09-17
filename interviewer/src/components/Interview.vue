<template>
    <div>
      <button @click="sendApiCall">Start Interview</button>
      <p v-if="responseData">{{ responseData }}</p>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import axios from 'axios';
  
  export default {
    setup() {
      const responseData = ref('');
  
      const sendApiCall = async () => {
        try {
          const response = await axios.post('http://localhost:8080/api/interviews', {
            "username": "Michael"
          });
          responseData.value = response.data.firstQuestion;
        } catch (error) {
          console.error("Error:", error);
          responseData.value = "API call failed";
        }
      };
  
      return {
        sendApiCall,
        responseData,
      };
    },
  };
  </script>