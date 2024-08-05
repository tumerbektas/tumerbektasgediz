<script setup>
import { ref } from 'vue';

const showContent = ref(false);
const isEnglish = ref(true);
const isDarkMode = ref(true); // Add a state for dark mode

const handleClick = () => {
  showContent.value = !showContent.value;
};

const switchLanguage = (language) => {
  isEnglish.value = language === 'en';
  showContent.value = false; // Reset content visibility when switching languages
};

const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value;
};
</script>

<template>
  <div :class="['container', { 'dark-mode': isDarkMode, 'light-mode': !isDarkMode }]">
    <div class="theme-toggle">
      <button @click="toggleTheme">Toggle Theme</button>
    </div>
    <div class="language-switch">
      <button @click="switchLanguage('en')" :class="{'active': isEnglish}">English</button>
      <button @click="switchLanguage('tr')" :class="{'active': !isEnglish}">Turkish</button>
    </div>
    <div class="centered">
      <div v-show="!showContent" class="classic-font fade-in" :class="{ 'slide-out-left': showContent }">
        {{ isEnglish ? 'Tümer Bektaş Gediz' : 'Tümer Bektaş Gediz' }}
      </div>
      <button v-show="!showContent" @click="handleClick" class="fade-in button">{{ isEnglish ? 'More' : 'Daha Fazla' }}</button>
      <div v-show="showContent" class="fade-in slide-in-right">
        <p class="subtitle fade-in">
          {{ isEnglish ? 'Computer Engineering Student, Software Developer.' : 'Bilgisayar Mühendisliği Öğrencisi, Yazılım Geliştirici.' }}
        </p>
        <p class="description fade-in">
          {{ isEnglish 
            ? "I'm Tümer, a senior student in Computer Engineering. I'm doing an internship in IT, System-Network, and Software Engineering fields and striving to develop myself professionally."
            : "Ben Tümer, Bilgisayar Mühendisliği son sınıf öğrencisiyim. IT, Sistem-Ağ ve Yazılım Mühendisliği alanlarında staj yapıyorum ve kendimi profesyonel olarak geliştirmeye çalışıyorum." }}
        </p>
        <div class="social-links">
          <div class="links fade-in">
            <div class="link-group">
              <h3>{{ isEnglish ? 'CONNECT' : 'BAĞLAN' }}</h3>
              <a href="mailto:gediztumer@gmail.com" target="_blank">Gmail</a>
              <a href="mailto:gediztumer@hotmail.com" target="_blank">Outlook</a>
            </div>
            <div class="link-group">
              <h3>{{ isEnglish ? 'SOCIAL' : 'SOSYAL' }}</h3>
              <a href="https://instagram.com/tumerbektasgediz" target="_blank">Instagram</a>
              <a href="https://x.com/tumerbektass" target="_blank">X</a>
              <a href="https://www.linkedin.com/in/tümer-bektaş-gediz-6753141b5/" target="_blank">Linkedin</a>
            </div>
            <div class="link-group">
              <h3>{{ isEnglish ? 'OTHER' : 'DİĞER' }}</h3>
              <a href="https://github.com/tumerbektas" target="_blank">GitHub</a>
              <a href="https://gitlab.com/gediztumer" target="_blank">GitLab</a>
              <a href="https://medium.com/@gediztumer" target="_blank">Medium</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <footer class="footer fade-in">
    © 2024 Tümer Bektaş Gediz
  </footer>
</template>

<style>
/* Global CSS */
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  background-color: #000000;
  color: #ffffff;
  font-family: 'Arial', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  position: relative; /* Ensures that footer positioning works */
  overflow: hidden; /* Hide overflow to remove scrollbars */
}

.dark-mode {
  background-color: #000000;
  color: #ffffff;
}

.light-mode {
  background-color: #ffffff;
  color: #000000;
}

.theme-toggle {
  position: absolute;
  top: 1rem;
  left: 1rem;
}

.language-switch {
  position: absolute;
  top: 1rem;
  right: 1rem;
  display: flex; /* Align buttons horizontally */
  gap: 0.5rem; /* Space between buttons */
}

.language-switch button, .theme-toggle button {
  background-color: transparent;
  color: inherit;
  border: 2px solid transparent; /* Border for active state */
  font-size: 1rem;
  cursor: pointer;
  padding: 0.5rem 1rem;
  font-family: 'Rawen'; /* Use the same font as the main text */
  transition: color 0.3s, border-color 0.3s; /* Smooth transition for color changes */
  border-radius: 8px; /* Kenarları yuvarlat */
}

.language-switch button.active {
  color: #d0d0d0;
  border-color: #d0d0d0; /* Border color for active button */
  font-weight: bold; /* Make the active language button bold */
}

.language-switch button:hover {
  color: #d0d0d0;
}

.centered {
  transform: translateY(-5%);
  padding: 1rem; /* Add padding for better spacing */
}

.classic-font {
  font-size: 6rem;
  font-family: 'Rawen';
  transition: opacity 0.5s ease-in-out, transform 0.5s ease-in-out; /* Smooth transition */
}

.button {
  margin-top: 1rem;
  font-size: 1.5rem;
  padding: 0.5rem 1rem;
  color: inherit; /* Use inherited text color */
  background-color: #000000; /* Arka plan rengi siyah */
  border: none;
  cursor: pointer;
  font-family: 'BGrove';
  border-radius: 8px; /* Kenarları yuvarlat */
  display: inline-block; /* Yazının üstüne tıklanabilir olması için */
}

.button:hover {
  background-color: #555555;
}

.subtitle, .description, .link-group {
  display: none; /* Initially hidden */
}

.fade-in {
  animation: fadeIn 2s ease-in-out forwards;
}

/* Slide-out animation */
@keyframes slideOutLeft {
  0% {
    transform: translateX(0);
    opacity: 1;
  }
  100% {
    transform: translateX(-100%);
    opacity: 0;
  }
}

/* Slide-in animation */
@keyframes slideInRight {
  0% {
    transform: translateX(100%);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

.slide-out-left {
  animation: slideOutLeft 0.5s forwards;
}

.slide-in-right {
  animation: slideInRight 0.5s forwards;
}

.subtitle {
  font-size: 2rem;
  font-family: 'Rawen'; /* Use the same font as the main text */
  margin-top: 0.5rem;
  display: block;
}

.description {
  font-size: 1.5rem;
  margin-top: 1rem;
  margin-left: auto;
  margin-right: auto;
  font-family: 'Rawen'; /* Use the same font as the main text */
  max-width: 90%;
  line-height: 1.5;
  display: block;
}

.social-links {
  margin-top: 3rem;
  display: block;
}

.links {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
}

.link-group {
  text-align: center;
  font-family: 'Rawen';
  display: block;
}

.link-group h3 {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
}

.link-group a {
  display: block;
  text-decoration: none;
  margin-bottom: 0.5rem;
}

.link-group a:hover {
  color: #d0d0d0;
}

/* Footer styles */
.footer {
  position: absolute;
  bottom: 1rem;
  left: 1rem;
  font-size: 0.9rem;
  font-weight: 300; /* Light font weight */
  font-family: 'Rawen'; /* Use a light-weight font if available */
}

.turkish-font {
  font-family: 'Comic Sans MS', sans-serif;
}

/* Font definitions */
@font-face {
  font-family: 'BGrove';
  src: url('./assets/bgrove.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: 'Rawen';
  src: url('./assets/RawengulkSans-094.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

/* Fade-in animation */
@keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
}
</style>
