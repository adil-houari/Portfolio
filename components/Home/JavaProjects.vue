<template>
    <div class="projects-grid">
        <!-- Example Project -->
        <div class="project-card" @click="openModal(projects[0])">
            <img :src="projects[0].image" alt="Project Screenshot" class="project-image" />
            <h3 class="project-title">{{ projects[0].title }}</h3>
            <p class="project-description">{{ projects[0].description }}</p>
        </div>

        <!-- Modal -->
        <div class="modal-overlay" v-if="selectedProject">
            <div class="modal-content">
                <button class="close-btn" @click="closeModal">&times;</button>
                <h2 class="modal-title">{{ selectedProject.title }}</h2>
                <img :src="selectedProject.image" alt="Project Screenshot" class="modal-image" />
                <p class="modal-description">{{ selectedProject.details }}</p>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

const projects = ref([
    {
        title: "VeilingPlatform",
        description: "A mobile auction platform developed in Java/Kotlin.",
        image: "/public/img/Adil.jpeg", 
        details:
            "VeilingPlatform is a mobile application for auctioning items, developed using Java/Kotlin. It includes features such as user authentication, real-time bidding, and payment integration.",
    },
]);

const selectedProject = ref(null);

const openModal = (project) => {
    selectedProject.value = project;
};

const closeModal = () => {
    selectedProject.value = null;
};
</script>

<style scoped>
.projects-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.project-card {
    background: #1e1e1e;
    border-radius: 15px;
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
    cursor: pointer;
    transition: transform 0.3s, box-shadow 0.3s;
    width: 300px;
    text-align: center;
    padding: 20px;
}

.project-card:hover {
    transform: scale(1.05);
    box-shadow: 0 8px 20px rgba(255, 77, 90, 0.6);
}

.project-image {
    width: 100%;
    border-radius: 10px;
    margin-bottom: 15px;
}

.project-title {
    font-size: 18px;
    color: #ff4d5a;
    margin-bottom: 10px;
}

.project-description {
    font-size: 14px;
    color: #ffffffcc;
}

.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.85);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
}

.modal-content {
    background: #1e1e1e;
    padding: 40px;
    border-radius: 20px;
    max-width: 600px;
    width: 90%;
    text-align: center;
    color: #ffffff;
}

.close-btn {
    position: absolute;
    top: 20px;
    right: 20px;
    background: transparent;
    border: none;
    font-size: 24px;
    color: #ffffff;
    cursor: pointer;
}

.close-btn:hover {
    color: #ff4d5a;
}

.modal-title {
    font-size: 24px;
    color: #ff4d5a;
    margin-bottom: 20px;
}

.modal-image {
    width: 100%;
    border-radius: 15px;
    margin-bottom: 15px;
}

.modal-description {
    font-size: 16px;
    color: #ffffffcc;
}
</style>