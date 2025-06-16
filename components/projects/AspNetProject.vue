<template>
    <div class="project-section">
        <h2 class="project-title">VeilingPlatform – ASP.NET API</h2>
        <p class="project-desc">
            A full-featured auction backend built with ASP.NET Core and fully tested using xUnit.
        </p>

        <ImageSliderWithModal :images="images" />




        <ul class="tech-stack">
            <li>ASP.NET Core</li>
            <li>Entity Framework</li>
            <li>SQL Server</li>
            <li>Swagger</li>
            <li>xUnit</li>
        </ul>

        <div class="project-links">
            <a href="https://github.com/AdilHouari/veiling-api" target="_blank">Voir le code</a>
        </div>
    </div>
</template>

<script setup>
import ImageSliderWithModal from "@/components/ui/ImageSliderWithModal.vue";

const images = [
    "/img/Velingc1.png",
    "/img/Velingc2.png",
    "/img/Velingc3.png",
    "/img/Velingc3.png",
];
</script>

<style scoped>
.project-section {
    padding: 80px 30px;
    background-color: #1e1e1e;
    margin-bottom: 60px;
    border-radius: 25px;
    box-shadow: 0 0 30px rgba(255, 77, 90, 0.2);
}

.project-title {
    font-size: 32px;
    color: #ff4d5a;
    margin-bottom: 20px;
    text-align: center;
}

.project-desc {
    font-size: 18px;
    color: #ffffffcc;
    margin-bottom: 30px;
    text-align: center;
}

.project-gallery {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
    margin-bottom: 30px;
}

.project-img {
    width: 100%;
    max-width: 500px;
    border-radius: 15px;
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.5);
    transition: transform 0.4s;
}

.project-img:hover {
    transform: scale(1.05);
}

.tech-stack {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 15px;
    margin-bottom: 20px;
}

.tech-stack li {
    list-style: none;
    background: #ff4d5a33;
    color: #fff;
    padding: 8px 16px;
    border-radius: 10px;
    font-size: 14px;
}

.project-links {
    text-align: center;
}

.project-links a {
    background-color: #ff4d5a;
    color: #fff;
    padding: 12px 30px;
    border-radius: 25px;
    text-decoration: none;
    font-weight: bold;
    transition: transform 0.3s;
}

.project-links a:hover {
    transform: scale(1.1);
}
</style>