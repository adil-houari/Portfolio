<template>
    <section class="projects-wrapper" id="work">
        <h2 class="section-title">My <span class="highlight">Projects</span></h2>
        <p class="section-subtitle">Here are a few projects I’ve worked on recently.</p>

        <AspNetProject />
        <KotlinProject />
    </section>
</template>

<script setup>
import AspNetProject from "@/components/projects/AspNetProject.vue";
import KotlinProject from "@/components/projects/KotlinProject.vue";
</script>

<style scoped>
.projects-wrapper {
    padding: 100px 60px;
    background-color: #0e0d0d;
    color: #fff;
    text-align: center;
}

.section-title {
    font-size: 42px;
    margin-bottom: 10px;
}

.section-subtitle {
    font-size: 20px;
    color: #ffffffcc;
    margin-bottom: 60px;
}

.highlight {
    color: #ff4d5a;
}
</style>