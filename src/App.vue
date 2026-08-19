<script setup>
import NavigationBar from './components/NavigationBar.vue'
import profilePicture from './assets/profile.jpg'
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
              href="https://www.linkedin.com/"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="LinkedIn"
            >
              in
            </a>

            <a
              href="https://www.jobstreet.com.ph/"
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

      <!-- Placeholder sections -->
      <section id="about" class="placeholder-section">
        <h2>About</h2>
      </section>

      <section id="skills" class="placeholder-section">
        <h2>Skills</h2>
      </section>

      <section id="portfolio" class="placeholder-section">
        <h2>Portfolio</h2>
      </section>

      <section id="contact" class="placeholder-section">
        <h2>Contact</h2>
      </section>
    </main>
  </div>
</template>
