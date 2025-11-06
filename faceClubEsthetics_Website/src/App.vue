<template>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap" rel="stylesheet">
<!-- Navigation Bar -->
  <nav class="navbar">
    <div class="navbar__container">
      <div class="navbar__heading">
        <h2>Join The Club</h2>
      </div>

      <!-- Mobile menu toggle -->
      <div
        id="mobile-menu"
        class="navbar__toggle"
        :class="{ 'is-active': mobileMenuActive }"
        @click="toggleMobileMenu"
      >
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </div>

      <!-- Menu items -->
      <ul :class="['navbar__menu', { active: mobileMenuActive }]">
        <li class="navbar__item"><button class="navbar__links" @click="currentSection = 'home'">Home</button></li>
        <li class="navbar__item"><button class="navbar__links" @click="currentSection = 'book'">Book Now</button></li>
        <li class="navbar__item"><button class="navbar__links" @click="currentSection = 'shop'">Shop</button></li>
        <li class="navbar__item"><button class="navbar__links" @click="currentSection = 'about'">About Me</button></li>
        <li class="navbar__item"><button class="navbar__links" @click="currentSection = 'contact'">Contact</button></li>
      </ul>
    </div>
  </nav>

  <!-- Main Page Content -->
  <div class="text_box">
    <h1 v-if="currentSection === 'home'">FaceClub Esthetics</h1>
    <h2 v-if="currentSection === 'home'">For Those Who Crave Results</h2>

    <div v-if="currentSection === 'book'">
      <h1>Book Your Appointment</h1>
      <p>Place Holder</p>
    </div>

    <div v-if="currentSection === 'shop'">
      <h1>Shop Products</h1>
      <p>Place Holder</p>
    </div>

    <div v-if="currentSection === 'about'">
      <h1>About Me</h1>
      <p>Place Holder</p>
    </div>

    <div v-if="currentSection === 'contact'">
      <h1>Contact</h1>
      <p>Place Holder</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Mobile menu state
const mobileMenuActive = ref(false)
function toggleMobileMenu() {
  mobileMenuActive.value = !mobileMenuActive.value
}

// Track which section is currently visible
const currentSection = ref('home')
</script>

<style scoped>
/* Paste all your styles from styles.css here */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Playfair Display", serif;
}

body {
  min-height: 100vh;
  background-image: linear-gradient(
      rgba(4, 9, 30, 0.1),
      rgba(4, 9, 30, 0.1)
    ),
    url('/image1.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
}

.navbar {
  background: #00000000;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.2rem;
  position: sticky;
  top: 0;
  z-index: 999;
}

.navbar__container {
  display: flex;
  justify-content: space-between;
  height: 80px;
  z-index: 1;
  width: 100%;
  max-width: 1300px;
  margin: 0 auto;
  padding: 0 50px;
}

.navbar__heading h2 {
  color: #fff;
  font-size: 1.5rem;
  align-items: center;
  justify-content: center;
  padding-top: 30px;
  font-weight: 300;
}

.navbar__menu {
  display: flex;
  align-items: center;
  list-style: none;
  text-align: center;
}

.navbar__item {
  height: 80px;
}

.navbar__links {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  padding: 0 1rem;
  height: 100%;
  cursor: pointer;
  background: none;
  border: none;
  font: inherit;
}

.navbar__links:hover {
  color: #800020;
  background-image: linear-gradient(to top, #800020 5%, #00000000 20%);
  transition: all 0.5s ease;
}

@media screen and (max-width: 960px) {
  .navbar__menu {
    display: grid;
    grid-template-columns: auto;
    margin: 0;
    width: 100%;
    position: absolute;
    top: -1000px;
    opacity: 0;
    transition: all 0.5s ease;
    height: 75vh;
    z-index: -1;
    background: #000000;
  }

  .navbar__menu.active {
    top: 100%;
    opacity: 1;
    z-index: 99;
  }

  .navbar__toggle .bar {
    width: 25px;
    height: 3px;
    margin: 5px auto;
    transition: all 0.3s ease;
    background: #fff;
    display: block;
    cursor: pointer;
  }

  #mobile-menu.is-active .bar:nth-child(2) {
    opacity: 0;
  }
  #mobile-menu.is-active .bar:nth-child(1) {
    transform: translateY(8px) rotate(45deg);
  }
  #mobile-menu.is-active .bar:nth-child(3) {
    transform: translateY(-8px) rotate(-45deg);
  }
}

.text_box {
  position: absolute;
  top: 20%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  text-align: center;
}

.text_box h1 {
  font-size: 2rem;
}

.text_box h2 {
  font-size: 1.2rem;
  font-weight: 300;
  margin-top: 10px;
}
</style>