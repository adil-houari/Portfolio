<template>
    <div class="hero">
        <div class="hero-content">
            <div class="hero-photo-container">
                <img src="/public/img/Adil.jpeg" alt="Adil Pic" class="hero-photo">
            </div>

            <!-- Hero Text -->
            <div class="hero-text">
                <div class="subtitle">Software Developer</div>
                <h1>Hello, I'm <span class="highlight">Adil Houari</span></h1>
                <p class="hero-description">
                    A passionate Software Engineer with expertise in Frontend and Backend Development, managing
                    databases, testing, and delivering high-quality code. I strive to bring innovation and efficiency to
                    every project I undertake.
                </p>

                <!-- Hero Buttons -->
                <div class="hero-buttons">
                    <button class="primary-btn">See My Work</button>
                    <button class="resume-btn" @click="openModal">Resume</button>
                </div>
            </div>
        </div>


        <!-- Resume Modal -->
        <div class="modal-backdrop" v-if="isModalOpen">
            <div class="modal-content">
                <button class="close-btn" @click="closeModal">&times;</button>
                <h2>Download My CV</h2>
                <p>Choose a language to download my CV:</p>
                <div class="modal-buttons">
                    <a href="/cv/Adil-Houari-CV-FR.pdf" download class="download-btn">French</a>
                    <a href="/cv/Adil-Houari-CV-NL.pdf" download class="download-btn">Dutch</a>
                    <a href="/cv/Adil-Houari-CV-ENG.pdf" download class="download-btn">English</a>
                </div>
            </div>
        </div>
    </div>
</template>


<!-- **************************************** JAVASCRIPT **************************************** -->
<!-- **************************************** JAVASCRIPT **************************************** -->
<!-- **************************************** JAVASCRIPT **************************************** -->
<script setup>
import { ref } from "vue";

const isModalOpen = ref(false);

// Open Modal
const openModal = () => {
    isModalOpen.value = true;
}

// Close Modal
const closeModal = () => {
    isModalOpen.value = false;
}
</script>


<!-- **************************************** scss **************************************** -->
<!-- **************************************** scss **************************************** -->
<!-- **************************************** scss **************************************** -->
<style scoped>
.hero {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #0e0d0d;
    color: #ffffff;
    padding: 0 60px;
}

.hero-content {
    display: flex;
    gap: 70px;
    align-items: center;
    max-width: 1400px;
    width: 100%;
}

.hero-photo-container {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
}

.hero-photo {
    width: 470px;
    height: 590px;
    border-radius: 20%;
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.5);
    transition: transform 0.4s ease, box-shadow 0.4s ease;
}

.hero-photo:hover {
    transform: scale(1.1) rotate(5deg);
    box-shadow: 0 8px 25px rgba(255, 77, 90, 0.8);
}

.hero-text {
    flex: 1;
}

.subtitle {
    font-size: 18px;
    color:#ff4d5a;
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 15px;
    display: inline-block;
    background: #ff4d5a33;
    padding: 5px 15px;
    border-radius: 15px;
    font-weight: bold;
    animation : fadeIn 1s ease-in-out;
}

h1 {
    font-size: 56px;
    margin-bottom: 20px;
}

h1 .highlight {
    color: #ff4d5a;
    position: relative;
    cursor: pointer;
    transition: color 0.3s ease, text-shadow 0.3s ease;
}

h1 .highlight:hover {
    color: #ffffff;
    text-shadow: 0 0 15px #ff4d5a, 0 0 30px #ff4d5a;
}

.hero-description {
    font-size: 22px;
    margin: 20px 0;
    color: #ffffffcc;
    line-height: 1.8;
}

.hero-buttons {
    display: flex;
    gap: 20px;
    margin-top: 25px;
}

/***** Buttons *****/ 
.primary-btn,
.resume-btn {
    padding: 15px 35px;
    border: none;
    border-radius: 35px;
    cursor: pointer;
    font-weight: bold;
    transition: transform 0.3s ease;
    font-size: 25px;
}

.primary-btn {
    background-color: #ff4d5a;
    color: #ffffff;
    transition: transform 0.3s, box-shadow 0.3s;
    box-shadow: 0 4px 15px rgba(255, 77, 90, 0.6), 0 0 10px rgba(255, 77, 90, 0.5);
}

.primary-btn:hover {
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8), 0 0 15px rgba(255, 77, 90, 0.7);
}

.resume-btn {
    background-color: transparent;
    color: #ff4d5a;
    border: 2px solid #ff4d5a;
}


.primary-btn:hover,
.resume-btn:hover {
    transform: translateY(-4px);
}

/* Modal Styles */
.modal-backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.85);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.modal-content {
    background-color: #1e1e1e;
    padding: 50px;
    border-radius: 30px;
    text-align: center;
    box-shadow: 0 6px 30px rgba(255, 77, 90, 0.8), 0 0 40px #ff4d5a;
    max-width: 700px;
    width: 90%;
    color: #ffffff;
    animation: blowUp 0.5s ease-out;
    position: relative;
}

.modal-content h2 {
    font-size: 36px;
    margin-bottom: 20px;
}

.modal-content p {
    font-size: 20px;
    margin-bottom: 40px;
}



.modal-buttons {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
}

.download-btn {
    background-color: #ff4d5a;
    color: #ffffff;
    text-decoration: none;
    padding: 15px 30px;
    border-radius: 30px;
    font-size: 20px;
    transition: background-color 0.3s, transform 0.3s;
}

.download-btn:hover {
    transform: scale(1.1);
}

.close-btn {
    position: absolute;
    top: 20px;
    right: 20px;
    background: transparent;
    border: none;
    font-size: 36px;
    color: #ffffff;
    cursor: pointer;
    transition: transform 0.3s ease, color 0.3s ease;
}

.close-btn:hover {
    transform: scale(1.2);
    color: #ff4d5a;
}

/******* ANIMATION  ********/

/* Animation blow-up */
@keyframes blowUp {
    0% {
        transform: scale(0.5);
        opacity: 0;
    }

    100% {
        transform: scale(1);
        opacity: 1;
    }
}

@keyframes fadeIn {
    0% {
        transform: scale(0.5);
        opacity: 0;
    }

    100% {
        transform: scale(1);
        opacity: 1;
    }
    
}
</style>
