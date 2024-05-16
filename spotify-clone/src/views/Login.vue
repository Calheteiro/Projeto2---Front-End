<template>
    <div class="flex flex-col gap-4 items-center justify-center h-full">
        <h1 class="text-[48px] font-bold text-white">Ligue a sua conta Spotify</h1>
      <button @click="login" class="bg-[#1BD760] text-[#282828] font-medium py-2 px-8 rounded-full">Login to Spotify</button>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      login() {
        const clientId = '440f1af43b6649678a695feffa55991f';
        const redirectUri = encodeURIComponent('http://localhost:5173/home');
        const scopes = encodeURIComponent('user-read-private user-read-email');
        window.location.href = `https://accounts.spotify.com/authorize?client_id=${clientId}&redirect_uri=${redirectUri}&scope=${scopes}&response_type=token&show_dialog=true`;
      }
    }
  }
  </script>
  