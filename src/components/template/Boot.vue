<template>
    <div>
      <!-- Loading Screen -->
      <div v-if="isLoading" class="loading-screen">
        <img src="@/assets/boot.gif" alt="Loading Spinner">
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isLoading: true
      };
    },
    mounted() {
      // Simulating a delay for demonstration purposes
      setTimeout(() => {
        // After the delay, set isLoading to false to hide the loading screen
        this.isLoading = false;
      }, 5000); // Adjust the time according to your preference
    }
  };
  </script>
  
  <style>
  .loading-screen {
    position: fixed;
    width: 100%;
    height: 100%;
    background-color: black;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
  }

.loading-screen img {
  filter: brightness(75%); /* Adjust the percentage to darken or lighten the GIF */
}
  </style>
  