<template>
    <div class="work-section" id="work-section">
        <!-- Section Title -->
        <div class="section-header">
            <h1 class="title">Projects that Make a Difference</h1>
            <p class="subtitle">Explore some of my finest work, crafted with passion and precision.</p>
        </div>

        <!-- Project Grid -->
        <div class="project-grid">
            <!-- Java/Kotlin Project Card -->
            <div class="project-card" @click="showProjectDetails('veilingplatform')">
                <img src="/public/img/Adil.jpeg" alt="Veilingplatform App" class="project-image" />
                <div class="project-info">
                    <h2 class="project-title">Veilingplatform</h2>
                    <p class="project-description">
                        A mobile auction platform built with Java and Kotlin for seamless user experience.
                    </p>
                    <div class="project-tags">
                        <span class="tag">Java</span>
                        <span class="tag">Kotlin</span>
                        <span class="tag">Android</span>
                    </div>
                </div>
            </div>

            <!-- Additional Project Cards can be added here -->
        </div>

        <!-- Project Details Modal -->
        <div class="project-modal" v-if="selectedProject">
            <div class="modal-content">
                <button class="close-btn" @click="closeModal">&times;</button>
                <h2 class="modal-title">{{ selectedProject.title }}</h2>
                <p class="modal-description">{{ selectedProject.description }}</p>

                <!-- Carousel for Screenshots -->
                <div class="carousel">
                    <img v-for="(image, index) in selectedProject.screenshots" :key="index" :src="image"
                        class="carousel-image" />
                </div>

                <!-- Action Buttons -->
                <div class="modal-actions">
                    <a :href="selectedProject.githubLink" target="_blank" class="action-btn">View on GitHub</a>
                    <a :href="selectedProject.demoLink" target="_blank" class="action-btn">Live Demo</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const selectedProject = ref(null);

// Example project data
const projects = [
    {
        id: 'veilingplatform',
        title: 'Veilingplatform',
        description: 'A mobile auction platform built with Java and Kotlin for seamless user experience.',
        screenshots: [
            '/public/img/Adil.jpeg',
            '/public/img/Adil.jpeg',
            '/public/img/Adil.jpeg',

        ],
        githubLink: 'https://github.com/your-profile/veilingplatform',
        demoLink: 'https://play.google.com/store/apps/details?id=veilingplatform',
    },
];

const showProjectDetails = (projectId) => {
    selectedProject.value = projects.find((project) => project.id === projectId);
};

const closeModal = () => {
    selectedProject.value = null;
};
</script>

<style scoped>
.work-section {
    padding: 100px 20px;
    background: linear-gradient(135deg, #0e0d0d, #1e1e1e);
    color: #fff;
    text-align: center;
}

.section-header {
    margin-bottom: 50px;
}

.title {
    font-size: 48px;
    color: #ff4d5a;
    animation: fadeInDown 1s ease;
}

.subtitle {
    font-size: 18px;
    color: #ffffffcc;
}

.project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 30px;
}

.project-card {
    background: #1e1e1e;
    border-radius: 15px;
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
    cursor: pointer;
    position: relative;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.6);
}

.project-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8);
}

.project-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.project-info {
    padding: 20px;
}

.project-title {
    font-size: 24px;
    color: #ff4d5a;
    margin-bottom: 10px;
}

.project-description {
    font-size: 16px;
    color: #ffffffcc;
    margin-bottom: 15px;
}

.project-tags .tag {
    display: inline-block;
    background: #ff4d5a;
    color: #fff;
    border-radius: 15px;
    padding: 5px 10px;
    margin-right: 5px;
    font-size: 14px;
}

.project-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.9);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.modal-content {
    background: #1e1e1e;
    padding: 40px;
    border-radius: 20px;
    text-align: center;
    max-width: 600px;
    width: 90%;
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.6);
}

.close-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    background: transparent;
    border: none;
    font-size: 30px;
    color: #ff4d5a;
    cursor: pointer;
}

.carousel {
    display: flex;
    overflow-x: scroll;
    gap: 10px;
    margin-top: 20px;
}

.carousel-image {
    max-height: 300px;
    border-radius: 10px;
    object-fit: cover;
}

.modal-actions .action-btn {
    display: inline-block;
    background: #ff4d5a;
    color: #fff;
    padding: 10px 20px;
    border-radius: 30px;
    margin: 10px;
    text-decoration: none;
    transition: transform 0.3s, box-shadow 0.3s;
}

.modal-actions .action-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8);
}

@keyframes fadeInDown {
    0% {
        opacity: 0;
        transform: translateY(-50px);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>