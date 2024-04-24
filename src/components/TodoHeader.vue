
<script setup>
    import { RouterLink } from 'vue-router';
</script>


<template>
    <div>
        <header>
            <nav class="container">
                <div class="branding">
                    <img src="../assets/Vue_Logo_Black.png" alt="vue logo image">
                    <h1>Vue Todos</h1>
                </div>
            </nav>
            <ul class="nav-routes">
                <RouterLink to="/">Home</RouterLink>
            </ul>
        </header>

    </div>
</template>


<style lang="scss" scoped>

</style>