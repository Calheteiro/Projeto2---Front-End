<template>
    <div v-if="userInfo">
      <h1>Welcome, {{ userInfo.display_name }}</h1>
      <img :src="userInfo.images[0].url" alt="profile image">
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        userInfo: null,
      };
    },
    methods: {
      fetchUserData(accessToken) {
        axios.get('https://api.spotify.com/v1/me', {
          headers: {
            'Authorization': `Bearer ${accessToken}`
          }
        })
        .then(response => {
          this.userInfo = response.data;
        })
        .catch(error => console.error("Error: ", error));
      }
    },
    created() {
      const hash = window.location.hash.substring(1);
      const params = new URLSearchParams(hash);
      const accessToken = params.get('access_token');
  
      if (accessToken) {
        this.fetchUserData(accessToken);
      }
    }
  }
  </script>
  