<template>
    <section class="skills-section" id="services">
        <h2 class="section-title">My <span class="highlight">Skills</span></h2>
        <p class="section-subtitle">Here’s a quick overview of my technical toolbox.</p>

        <div class="skills-grid">
            <div class="skill-card" v-for="skill in skills" :key="skill.name">
                <div class="icon-container" :style="{ backgroundColor: skill.color }">
                    <i :class="skill.icon"></i>
                </div>
                <h3>{{ skill.name }}</h3>
                <p>{{ skill.level }}</p>
            </div>
        </div>
    </section>
</template>

<script setup>
const skills = [
    { name: 'Vue.js', level: 'Advanced', icon: 'fab fa-vuejs', color: '#42b883' },
    { name: 'Nuxt.js', level: 'Advanced', icon: 'fab fa-nuxt-js', color: '#00dc82' },
    { name: 'Java', level: 'Proficient', icon: 'fab fa-java', color: '#e11d48' },
    { name: 'Kotlin', level: 'Proficient', icon: 'fas fa-code', color: '#a78bfa' },
    { name: 'C# / ASP.NET', level: 'Proficient', icon: 'fas fa-laptop-code', color: '#8b5cf6' },
    { name: 'PHP', level: 'Good', icon: 'fab fa-php', color: '#4F5B93' },
    { name: 'MySQL', level: 'Good', icon: 'fas fa-database', color: '#fcd34d' },
    { name: 'MongoDB', level: 'Basic', icon: 'fas fa-leaf', color: '#10b981' },
    { name: 'Git / Docker', level: 'Good', icon: 'fab fa-git-alt', color: '#f97316' }
];
</script>

<style scoped>
.skills-section {
    padding: 100px 60px;
    background: linear-gradient(135deg, #0e0d0d, #1e1e1e);
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
    margin-bottom: 50px;
}

.highlight {
    color: #ff4d5a;
}

.skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 30px;
}

.skill-card {
    background: #1e1e1e;
    padding: 30px;
    border-radius: 20px;
    transition: transform 0.4s ease, box-shadow 0.4s ease;
    box-shadow: 0 0 15px rgba(255, 77, 90, 0.3);
}

.skill-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 0 25px rgba(255, 77, 90, 0.5);
}

.icon-container {
    width: 60px;
    height: 60px;
    margin: 0 auto 20px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 26px;
    box-shadow: 0 0 10px #ff4d5a;
}

.skill-card h3 {
    font-size: 20px;
    margin-bottom: 8px;
}

.skill-card p {
    font-size: 14px;
    color: #ffffffcc;
}
</style>