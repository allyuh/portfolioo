<script setup>
import NavigationBar from './components/NavigationBar.vue'
import profilePicture from './assets/profile.jpg'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ContactSection from './components/ContactSection.vue'
</script>

<template>
  <div class="website">
    <NavigationBar />

    <main>
      <section id="home" class="hero home-section">

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
              href="https://ph.jobstreet.com/profiles/allyanna-mejia-qKvqVYrtWJ"
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

        <div class="hero-image">
          <img :src="profilePicture" alt="Allyanna Mejia" />
        </div>
      </section>

      <AboutSection />
      <SkillsSection />
      <PortfolioSection />
      <ContactSection />

    </main>
  </div>
</template>
