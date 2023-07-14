<template>
    <div>
        <h1>About Us</h1>
        <p>This is the about page content for my rigelis test work.</p>
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-4" @click="goToHome">Go to
            Home
        </button>
    </div>
</template>
  
<script>
export default {
    name: 'About',
    methods: {
        goToHome() {
            this.$router.push('/');
        },
    }
};
</script>
  
<style scoped>
/* Add component-specific styles here if needed */
</style>
  