<template>
    <div>
        <!-- Header -->
        <header class="header">
            <div class="logo">
                <span class="logo-dot">●</span> MyPortfolio
            </div>
            <nav class="nav-links">
                <a href="#home" class="nav-item">Home</a>
                <a href="#services" class="nav-item">Skills</a>

                <!-- Resume Dropdown -->
                <div class="dropdown-container" @mouseover="openDropdown" @mouseleave="closeDropdown">
                    <a href="#resume" class="nav-item">
                        Resume
                        <i class="arrow-down"></i>
                    </a>
                    <div class="dropdown" v-if="dropdownOpen">
                        <a href="/cv/Adil-Houari-CV-FR.pdf" download class="dropdown-item">
                            <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                                <path fill="currentColor"
                                    d="M12 21q-.425 0-.713-.288Q11 20.425 11 20v-8.575L9.125 13.4q-.3.3-.7.3t-.7-.3q-.3-.3-.3-.7t.3-.7l3.6-3.6q.15-.15.325-.213q.175-.062.375-.062q.2 0 .375.062q.175.063.325.213l3.6 3.6q.3.3.3.7t-.3.7q-.3.3-.7.3t-.7-.3L13 11.425V20q0 .425-.287.712Q12.425 21 12 21Zm-6 0q-.825 0-1.413-.588Q4 19.825 4 19v-2q0-.425.288-.713Q4.575 16 5 16t.713.287Q6 16.575 6 17v2h12v-2q0-.425.288-.713Q18.575 16 19 16t.712.287Q20 16.575 20 17v2q0 .825-.588 1.412Q18.825 21 18 21Z" />
                            </svg>
                            French
                        </a>
                        <a href="/cv/Adil-Houari-CV-NL.pdf" download class="dropdown-item">
                            <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                                <path fill="currentColor"
                                    d="M12 21q-.425 0-.713-.288Q11 20.425 11 20v-8.575L9.125 13.4q-.3.3-.7.3t-.7-.3q-.3-.3-.3-.7t.3-.7l3.6-3.6q.15-.15.325-.213q.175-.062.375-.062q.2 0 .375.062q.175.063.325.213l3.6 3.6q.3.3.3.7t-.3.7q-.3.3-.7.3t-.7-.3L13 11.425V20q0 .425-.287.712Q12.425 21 12 21Zm-6 0q-.825 0-1.413-.588Q4 19.825 4 19v-2q0-.425.288-.713Q4.575 16 5 16t.713.287Q6 16.575 6 17v2h12v-2q0-.425.288-.713Q18.575 16 19 16t.712.287Q20 16.575 20 17v2q0 .825-.588 1.412Q18.825 21 18 21Z" />
                            </svg>
                            Dutch
                        </a>
                        <a href="/cv/Adil-Houari-CV-ENG.pdf" download class="dropdown-item">
                            <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                                <path fill="currentColor"
                                    d="M12 21q-.425 0-.713-.288Q11 20.425 11 20v-8.575L9.125 13.4q-.3.3-.7.3t-.7-.3q-.3-.3-.3-.7t.3-.7l3.6-3.6q.15-.15.325-.213q.175-.062.375-.062q.2 0 .375.062q.175.063.325.213l3.6 3.6q.3.3.3.7t-.3.7q-.3.3-.7.3t-.7-.3L13 11.425V20q0 .425-.287.712Q12.425 21 12 21Zm-6 0q-.825 0-1.413-.588Q4 19.825 4 19v-2q0-.425.288-.713Q4.575 16 5 16t.713.287Q6 16.575 6 17v2h12v-2q0-.425.288-.713Q18.575 16 19 16t.712.287Q20 16.575 20 17v2q0 .825-.588 1.412Q18.825 21 18 21Z" />
                            </svg>
                            English
                        </a>
                    </div>
                </div>

                <a href="#work" class="nav-item">Work</a>
                <router-link to="/contact" class="nav-item">Contact</router-link>
            </nav>

            <!-- Hire Me Button -->
            <button class="hire-me-btn" @click="openModal">Hire Me</button>
        </header>

        <!-- Modal -->
        <div class="modal-backdrop" v-if="isModalOpen">
            <div class="modal-content">
                <button class="close-btn" @click="closeModal">&times;</button>
                <h2>Contact Me via Email</h2>
                <p>
                    Clicking the button below will open your email client so you can write to me directly.
                    Whether you're looking to collaborate, have questions, or want to know more, feel free to get in
                    touch!
                </p>
                <div class="modal-buttons">
                    <a href="mailto:Adil.Houari@outlook.com?subject=Interested%20in%20collaborating" class="email-btn">
                        Open Email
                    </a>
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

const dropdownOpen = ref(false);
const isModalOpen = ref(false);


// Dropdown
const openDropdown = () => {
    dropdownOpen.value = true;
};

const closeDropdown = () => {
    dropdownOpen.value = false;
};


//  Modal
const openModal = () => {
    isModalOpen.value = true;
};

const closeModal = () => {
    isModalOpen.value = false;
};

</script>


<style scoped>
/* Header */
.header {
    box-sizing: border-box;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 60px;
    background-color: #0e0d0d;
    color: #ffffff;
    width: 100%;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    backdrop-filter: blur(10px);
    position: fixed;
    top: 0;
    z-index: 1000;
    transition: background-color 0.3s;
}

.logo {
    font-size: 32px;
    font-weight: bold;
    color: #ffffff;
    display: flex;
    align-items: center;
}

.logo-dot {
    color: #ff4d5a;
    font-size: 34px;
    line-height: 0;
    margin-right: 8px;
}

/* Navigation links */
.nav-links {
    display: flex;
    gap: 30px;
    position: relative;
}

.nav-item {
    color: #ffffff;
    text-decoration: none;
    font-size: 18px;
    font-weight: 500;
    position: relative;
    transition: color 0.3s;
}

/* Ajouter le hover avec la barre */
.nav-item::after {
    content: '';
    display: block;
    width: 0;
    height: 2px;
    background: #ff4d5a;
    transition: width 0.4s cubic-bezier(0.25, 1, 0.5, 1);
    position: absolute;
    bottom: -5px;
    left: 0;
}

.nav-item:hover {
    color: #ff4d5a;
}

.nav-item:hover::after {
    width: 100%;
}

/* Hire Me Button */
.hire-me-btn {
    background-color: #ff4d5a;
    color: #ffffff;
    border: none;
    padding: 12px 30px;
    border-radius: 30px;
    cursor: pointer;
    font-size: 18px;
    font-weight: bold;
    transition: transform 0.3s, box-shadow 0.3s;
    box-shadow: 0 4px 15px rgba(255, 77, 90, 0.6), 0 0 10px rgba(255, 77, 90, 0.5);
}

.hire-me-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8), 0 0 15px rgba(255, 77, 90, 0.7);
}

/* Dropdown Container */
.dropdown-container {
    position: relative;
}

/* Dropdown Menu */
.dropdown {
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #1e1e1e;
    padding: 15px 0;
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
    z-index: 1000;
    animation: fadeIn 0.3s ease-in-out;
}

/* Dropdown Items */
.dropdown-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 10px 20px;
    text-decoration: none;
    font-size: 16px;
    color: #ffffff;
    transition: background-color 0.3s ease, transform 0.3s ease;
}

.dropdown-item:hover {
    background-color: #d62828;
    border-radius: 8px;
    transform: translateX(5px);
    box-shadow: 0 4px 15px rgba(214, 40, 40, 0.6);
}

/* Icône SVG */
.icon {
    width: 20px;
    height: 20px;
    fill: #ff4d5a;
    transition: transform 0.3s, filter 0.3s ease-in-out;
    filter: drop-shadow(0 0 5px #ff4d5a);
}

.dropdown-item:hover .icon {
    transform: scale(1.3);
    filter: drop-shadow(0 0 15px #ff4d5a);
}



/* Arrow Down Icon */
.arrow-down {
    margin-left: 5px;
    font-size: 12px;
    color: #ffffffcc;
    border: solid #ffffffcc;
    border-width: 0 2px 2px 0;
    display: inline-block;
    padding: 3px;
    transform: rotate(45deg);
    transition: transform 0.3s;
}

.nav-item:hover .arrow-down {
    transform: rotate(-135deg);
}

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
    max-width: 600px;
    width: 90%;
    color: #ffffff;
    animation: blowUp 0.4s ease-out;
    position: relative;
    transform: translateY(0);
}


.modal-content h2 {
    font-size: 32px;
    margin-bottom: 15px;
}

.modal-content p {
    font-size: 18px;
    margin-bottom: 30px;
    color: #ffffffcc;
}

/* Button styles */
.email-btn {
    background-color: #ff4d5a;
    color: #ffffff;
    text-decoration: none;
    padding: 15px 30px;
    border-radius: 30px;
    font-size: 18px;
    transition: transform 0.3s, box-shadow 0.3s;
}

.email-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8), 0 0 15px rgba(255, 77, 90, 0.7);
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

/*****  Animation *****/
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
        opacity: 0;
        transform: translateY(-10px);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>
