<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('home')
const menuOpen = ref(false)

const sections = ['home', 'about', 'skills', 'portfolio', 'contact']

const updateActiveSection = () => {
  const scrollPosition = window.scrollY + 200

  for (const section of sections) {
    const element = document.getElementById(section)

    if (element) {
      const sectionTop = element.offsetTop
      const sectionBottom = sectionTop + element.offsetHeight

      if (scrollPosition >= sectionTop && scrollPosition < sectionBottom) {
        activeSection.value = section
        break
      }
    }
  }
}

const closeMenu = () => {
  menuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', updateActiveSection)
  updateActiveSection()
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateActiveSection)
})
</script>

<template>
  <nav
    class="navbar"
    :class="{
      'navbar-dark': activeSection === 'home',
      'navbar-light': activeSection !== 'home',
    }"
  >
    <div class="nav-container">
      <!-- logo -->
      <a href="#home" class="logo" @click="closeMenu">
        <span>Allyanna Mejia</span>
        <span class="logo-hover-text"></span>
      </a>

      <!-- hamburger -->
      <button
        class="hamburger"
        :class="{ open: menuOpen }"
        @click="menuOpen = !menuOpen"
        aria-label="Toggle navigation menu"
        :aria-expanded="menuOpen"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <!-- navbar -->
      <ul class="nav-links" :class="{ 'menu-open': menuOpen }">
        <li>
          <a href="#home" :class="{ active: activeSection === 'home' }" @click="closeMenu">
            <span>Home</span>
            <span class="nav-hover-text">Home</span>
          </a>
        </li>

        <li>
          <a href="#about" :class="{ active: activeSection === 'about' }" @click="closeMenu">
            <span>About</span>
            <span class="nav-hover-text">About</span>
          </a>
        </li>

        <li>
          <a href="#skills" :class="{ active: activeSection === 'skills' }" @click="closeMenu">
            <span>Skill</span>
            <span class="nav-hover-text">Skill</span>
          </a>
        </li>

        <li>
          <a
            href="#portfolio"
            :class="{ active: activeSection === 'portfolio' }"
            @click="closeMenu"
          >
            <span>Resume</span>
            <span class="nav-hover-text">Resume</span>
          </a>
        </li>

        <li>
          <a href="#contact" :class="{ active: activeSection === 'contact' }" @click="closeMenu">
            <span>Contact</span>
            <span class="nav-hover-text">Contact</span>
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>
