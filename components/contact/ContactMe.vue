<template>
    <div class="contact-page">
        <!-- Back to Home Button -->
        <button class="back-btn" @click="goHome">← Home</button>

        <!-- Floating Decorative Elements -->
        <div class="floating-element floating-top-left"></div>
        <div class="floating-element floating-bottom-right"></div>

        <!-- Left Section: Social Links -->
        <div class="contact-left">
            <h2>Let's Connect</h2>
            <p>
                Feel free to reach out via social media or send me a message directly.
            </p>
            <SocialLinks />
        </div>

        <!-- Right Section: Contact Form -->
        <form class="contact-form" @submit.prevent="handleSubmit">
            <h1>Contact Me</h1>
            <div class="form-group" v-for="(value, key) in formData" :key="key"
                :class="{ 'has-error': validationErrors[key] }">
                <label :for="key">{{ key === 'message' ? 'Message' : 'Your ' + key.charAt(0).toUpperCase() + key.slice(1) }}</label>
                <textarea v-if="key === 'message'" :id="key" v-model="formData[key]" :placeholder="'Enter your ' + key" rows="5" @blur="validateField(key)"></textarea>
                <input v-else :id="key" v-model="formData[key]" :placeholder="'Enter your ' + key" @blur="validateField(key)" :type="key === 'email' ? 'email' : 'text'" />
                <!-- Error Message -->
                <div class="error-message" v-if="validationErrors[key]">{{ validationErrors[key] }}</div>
            </div>
            <button type="submit" class="send-btn">Send Message</button>
        </form>

        <!-- Success Animation -->
        <div class="success-overlay" v-if="successMessage">
            <div class="success-message">
                <p>Your message has been sent successfully!</p>
            </div>
        </div>
    </div>
</template>

<!-- **************************************** JAVASCRIPT **************************************** -->
<!-- **************************************** JAVASCRIPT **************************************** -->
<!-- **************************************** JAVASCRIPT **************************************** -->

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router"; // Import Vue Router
import SocialLinks from "@/components/socialLinks.vue";
import emailjs from "@emailjs/browser";

const formData = ref({
    name: "",
    email: "",
    subject: "",
    message: "",
});

const validationErrors = ref({});
const successMessage = ref(false);
const router = useRouter(); 

const goHome = () => {
    router.push("/"); // Navigate back to the home page
};

const validateField = (field) => {
    if (!formData.value[field]) {
        validationErrors.value[field] = `${field.charAt(0).toUpperCase() + field.slice(1)} is required`;
    } else {
        validationErrors.value[field] = null;
    }
};

const handleSubmit = async () => {
    // Validate all fields
    Object.keys(formData.value).forEach((key) => validateField(key));

    if (Object.values(validationErrors.value).some((error) => error)) {
        return; // Stop submission if there are errors
    }

    const emailParams = {
        from_name: formData.value.name,
        from_email: formData.value.email,
        subject: formData.value.subject,
        message: formData.value.message,
    };

    try {
        await emailjs.send(
            "service_f4mjyyb",
            "template_ovf1h6b",
            emailParams,
            "MOTzY2QkA7b7or6sw"
        );

        successMessage.value = true;

        // Hide animation after 3 seconds
        setTimeout(() => {
            successMessage.value = false;
        }, 3000);

        // Reset form
        formData.value = {
            name: "",
            email: "",
            subject: "",
            message: "",
        };
    } catch (error) {
        console.error("Failed to send message:", error);
    }
};
</script>


<!-- **************************************** scss **************************************** -->
<!-- **************************************** scss **************************************** -->
<!-- **************************************** scss **************************************** -->
<style scoped>
.contact-page {
    display: flex;
    justify-content: space-between;
    align-items: center;
    min-height: 100vh;
    background: linear-gradient(135deg, #0e0d0d, #1e1e1e);
    padding: 30px 50px;
    /* Reduced padding for better alignment */
    position: relative;
    overflow: hidden;
}

/* Back to Home Button */
.back-btn {
    position: absolute;
    top: 20px;
    left: 20px;
    padding: 12px 25px;
    border-radius: 30px;
    border: none;
    background: transparent;
    color: #ff4d5a;
    font-size: 16px;
    cursor: pointer;
    font-weight: bold;
    transition: transform 0.3s, box-shadow 0.3s, color 0.3s;
    z-index: 9999;
}

.back-btn:hover {
    color: #ffffff;
    background-color: #ff4d5a;
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8), 0 0 15px rgba(255, 77, 90, 0.7);
}

/* Floating Decorative Elements */
.floating-element {
    position: absolute;
    border-radius: 50%;
    background: #ff4d5a1a;
    z-index: 1;
    animation: pulse 4s infinite;
}

.floating-top-left {
    top: 10%;
    left: -10%;
    width: 200px;
    height: 200px;
}

.floating-bottom-right {
    bottom: 5%;
    right: -15%;
    width: 300px;
    height: 300px;
}

/* Left Section */
.contact-left {
    flex: 1;
    padding: 30px;
    margin-top: -40px;
    color: #ffffff;
    z-index: 2;
}

.contact-left h2 {
    font-size: 36px;
    color: #ff4d5a;
    margin-bottom: 20px;
}

.contact-left p {
    font-size: 18px;
    color: #ffffffcc;
    margin-bottom: 30px;
}

.contact-left .social-links {
    display: flex;
    gap: 15px;
}

/* Right Section: Contact Form */
.contact-form {
    flex: 1.5;
    background: #1e1e1e;
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.6);
    z-index: 2;
    animation: fadeInRight 1s ease-in-out;
    margin-top: -40px;
}

.contact-form h1 {
    font-size: 36px;
    color: #ff4d5a;
    margin-bottom: 20px;
}

.form-group {
    margin-bottom: 20px;
    display: flex;
    flex-direction: column;
}

.form-group label {
    font-size: 16px;
    color: #ff4d5a;
    margin-bottom: 5px;
}

.form-group input,
.form-group textarea {
    width: 97%;
    padding: 12px;
    border-radius: 10px;
    border: 1px solid #ffffff33;
    background-color: #0e0d0d;
    color: #ffffff;
    font-size: 16px;
    outline: none;
    transition: border-color 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
    border-color: #ff4d5a;
    box-shadow: 0 0 10px #ff4d5a;
}

.error-message {
    font-size: 14px;
    color: #ff4d5a;
    margin-top: 5px;
}

.send-btn {
    width: 100%;
    padding: 15px;
    border: none;
    border-radius: 30px;
    background-color: #ff4d5a;
    color: #ffffff;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(255, 77, 90, 0.6), 0 0 10px rgba(255, 77, 90, 0.5);
    transition: transform 0.3s, box-shadow 0.3s;
}

.send-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(255, 77, 90, 0.8), 0 0 15px rgba(255, 77, 90, 0.7);
}

/* Success Animation */
.success-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding-top: 100px;
    z-index: 9999;
}

.success-message {
    background: #1e1e1e;
    padding: 20px 40px;
    border-radius: 20px;
    text-align: center;
    color: #ff4d5a;
    font-size: 20px;
    animation: fadeInOut 3s ease-in-out;
}

/* Animation for Success Message */
@keyframes fadeInRight {
    0% {
        opacity: 0;
        transform: translateX(50px);
    }

    100% {
        opacity: 1;
        transform: translateX(0);
    }
}

@keyframes pulse {

    0%,
    100% {
        transform: scale(1);
    }

    50% {
        transform: scale(1.2);
    }
}
</style>
