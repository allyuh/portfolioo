<script setup>
import NavigationBar from './components/NavigationBar.vue'
import profilePicture from './assets/profile.jpg'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
</script>

<template>
  <div class="website">
    <NavigationBar />

    <main>
      <section id="home" class="hero home-section">
        <!-- Left Side -->
        <div class="hero-text">
          <p class="greeting">Get to know me!</p>

          <h1>
            Hi, my name is
            <span>Allyanna Mejia</span>
          </h1>

          <h2>An aspiring Web Developer</h2>

          <p class="description">
            Welcome to my portfolio. You can know more about me by exploring my website!
          </p>

          <!-- Social / Job Links -->
          <div class="social-links">
            <a
              href="https://www.linkedin.com/in/allya07/"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="LinkedIn"
            >
              in
            </a>

            <a
              href="ph.jobstreet.com/profiles/allyanna-mejia-qKvqVYrtWJ"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="JobStreet"
            >
              JS
            </a>

            <a
              href="https://ph.indeed.com/"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="Indeed"
            >
              i
            </a>
          </div>
        </div>

        <!-- Right Side -->
        <div class="hero-image">
          <img :src="profilePicture" alt="Allyanna Mejia" />
        </div>
      </section>

      <AboutSection />

      <SkillsSection />

      <section id="portfolio" class="placeholder-section">
        <h2>Portfolio</h2>
      </section>

      <section id="contact" class="placeholder-section">
        <h2>Contact</h2>
      </section>
    </main>
  </div>
</template>
