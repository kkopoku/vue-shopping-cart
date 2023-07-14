<template>
    <div>
        <h1>Welcome to the Home Page</h1>
        <p>This is the content of the home page.</p>
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-4" @click="goToAbout">Go to
            About</button>
    </div>
</template>
  
<script>
export default {
    name: 'Home',
    methods: {
        goToAbout() {
            this.$router.push('/about');
        },
    },
};
</script>
  
<style>
/* Add component-specific styles here if needed */
</style>
  