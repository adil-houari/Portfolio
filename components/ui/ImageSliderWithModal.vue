<template>
    <div class="carousel-container">
        <!-- Image Wrapper -->
        <div class="carousel-wrapper">
            <div v-for="(img, index) in images" :key="index" class="carousel-item"
                :class="{ 'active': index === activeIndex }" @click="openModal(index)">
                <img :src="img" alt="project image" />
            </div>
        </div>

        <!-- Navigation dots -->
        <div class="dots">
            <span v-for="(img, i) in images" :key="i" :class="{ active: i === activeIndex }"
                @click="goToSlide(i)"></span>
        </div>

        <!-- Modal Viewer -->
        <div class="modal" v-if="isModalOpen" @click.self="closeModal">
            <button class="close" @click="closeModal">&times;</button>
            <img :src="images[modalIndex]" class="modal-img" />
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
    images: Array
})

const activeIndex = ref(0)
const isModalOpen = ref(false)
const modalIndex = ref(0)

const openModal = (index) => {
    modalIndex.value = index
    isModalOpen.value = true
}

const closeModal = () => {
    isModalOpen.value = false
}

const goToSlide = (index) => {
    activeIndex.value = index
}

onMounted(() => {
    setInterval(() => {
        activeIndex.value = (activeIndex.value + 1) % props.images.length
    }, 1000)
})
</script>

<style scoped>
.carousel-container {
    overflow: hidden;
    position: relative;
    max-width: 100%;
    padding: 60px 0;
}

.carousel-wrapper {
    display: flex;
    gap: 40px;
    padding: 10px 30px;
    scroll-behavior: smooth;
    justify-content: center;
}

.carousel-item {
    flex: 0 0 auto;
    width: 350px;
    height: 220px;
    transition: transform 0.6s ease, opacity 0.5s;
    transform-style: preserve-3d;
    cursor: pointer;
    opacity: 0.6;
    perspective: 1000px;
    position: relative;
}

.carousel-item.active {
    opacity: 1;
    transform: scale(1.05) rotateY(0deg);
    z-index: 2;
}

.carousel-item:hover {
    transform: scale(1.1) rotateY(2deg);
    opacity: 1;
}

.carousel-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 20px;
    box-shadow: 0 8px 20px rgba(255, 77, 90, 0.5);
}

.dots {
    display: flex;
    justify-content: center;
    margin-top: 25px;
    gap: 10px;
}

.dots span {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: #888;
    cursor: pointer;
    transition: background 0.3s ease;
}

.dots span.active {
    background-color: #ff4d5a;
    box-shadow: 0 0 8px #ff4d5a;
}

.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.85);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 999;
    animation: fadeIn 0.5s ease forwards;
}

.modal-img {
    max-width: 90vw;
    max-height: 90vh;
    border-radius: 20px;
    box-shadow: 0 0 40px rgba(255, 77, 90, 0.6);
}

.close {
    position: absolute;
    top: 30px;
    right: 40px;
    font-size: 36px;
    color: #fff;
    background: transparent;
    border: none;
    cursor: pointer;
    transition: 0.3s;
}

.close:hover {
    color: #ff4d5a;
    transform: scale(1.2);
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: scale(0.92);
    }

    to {
        opacity: 1;
        transform: scale(1);
    }
}
</style>