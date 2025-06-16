<template>
    <div class="social-links">
        <a href="https://www.linkedin.com/in/adil-houari-1b3328255/" target="_blank" class="social-icon">
            <img src="/img/linkedin.png" alt="LinkedIn" class="icon">
        </a>
    </div>
</template>

<script setup>
</script>


<!-- **************************************** scss **************************************** -->
<!-- **************************************** scss **************************************** -->
<!-- **************************************** scss **************************************** -->

<style scoped>
.social-links {
    display: flex;
    gap: 15px;
    justify-content: center;
    margin-top: 20px;
}

.social-icon {
    display: inline-block;
    width: 50px; 
    height: 50px; 
    position: relative; 
    overflow: hidden; 
    border-radius: 15%; 
    box-shadow: 0 0 10px #ff4d5a, 0 0 20px #ff4d5a; 
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.social-icon:hover {
    transform: scale(1.1); 
    box-shadow: 0 0 20px #ff4d5a, 0 0 40px #ff4d5a; 
    animation: neonPulse 1.5s infinite; 
}
.icon {
    width: 100%; 
    height: 100%; 
    object-fit: cover; 
    transition: transform 0.5s ease;
}

/* Animation pour l'effet lumineux */
@keyframes neonPulse {
    0% {
        box-shadow: 0 0 10px #ff4d5a, 0 0 20px #ff4d5a;
    }
    50% {
        box-shadow: 0 0 30px #ff4d5a, 0 0 60px #ff4d5a;
    }
    100% {
        box-shadow: 0 0 10px #ff4d5a, 0 0 20px #ff4d5a;
    }
}
</style>
