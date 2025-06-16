<template>
    <div class="carousel-container">
        <button class="arrow left" @click="prevSlide" v-if="canSlideLeft">‹</button>

        <div class="carousel-track">
            <div class="carousel-slide" v-for="(image, index) in images" :key="index"
                :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
                <img :src="image" class="carousel-img" @click="nextSlide" />
            </div>
        </div>

        <button class="arrow right" @click="nextSlide" v-if="canSlideRight">›</button>
    </div>
</template>

<script setup>
import { ref, computed } from "vue";

const props = defineProps({
    images: {
        type: Array,
        required: true
    }
});

const currentIndex = ref(0);
const maxVisible = 3;

const totalGroups = computed(() =>
    Math.ceil(props.images.length / maxVisible)
);

const canSlideLeft = computed(() => currentIndex.value > 0);
const canSlideRight = computed(() => currentIndex.value < totalGroups.value - 1);

const nextSlide = () => {
    if (canSlideRight.value) currentIndex.value++;
};

const prevSlide = () => {
    if (canSlideLeft.value) currentIndex.value--;
};
</script>

<style scoped>
.carousel-container {
    position: relative;
    overflow: hidden;
    width: 100%;
    max-width: 1000px;
    margin: auto;
}

.carousel-track {
    display: flex;
    transition: transform 0.6s ease;
    width: 100%;
}

.carousel-slide {
    flex: 0 0 33.3333%;
    padding: 0 10px;
    box-sizing: border-box;
}

.carousel-img {
    width: 100%;
    border-radius: 15px;
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.5);
    cursor: pointer;
    transition: transform 0.3s ease;
}

.carousel-img:hover {
    transform: scale(1.05);
}

.arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255, 77, 90, 0.2);
    border: 2px solid #ff4d5a;
    color: #ff4d5a;
    font-size: 30px;
    font-weight: bold;
    border-radius: 50%;
    padding: 10px 16px;
    cursor: pointer;
    z-index: 10;
    transition: background 0.3s, transform 0.3s;
}

.arrow:hover {
    background: #ff4d5a;
    color: #fff;
    transform: translateY(-50%) scale(1.1);
}

.left {
    left: -10px;
}

.right {
    right: -10px;
}
</style>