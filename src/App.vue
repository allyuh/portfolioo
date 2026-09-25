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
            Welcome to my portfolio. You can know more about me by exploring this website!
          </p>

          <div class="social-links">

            <a
              href="https://www.linkedin.com/in/allya07/"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="LinkedIn"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                aria-hidden="true"
              >
                <path
                  d="M6.5 8.5H3V21h3.5V8.5ZM4.75 3A2.05 2.05 0 1 0 4.75 7.1 2.05 2.05 0 0 0 4.75 3ZM21 13.8c0-3.76-2-5.5-4.67-5.5-2.15 0-3.11 1.18-3.65 2v-1.8H9.2V21h3.48v-6.2c0-1.64.31-3.23 2.34-3.23 2 0 2.03 1.88 2.03 3.34V21H21v-7.2Z"
                />
              </svg>
            </a>


              <a
                href="https://ph.jobstreet.com/profiles/allyanna-mejia-qKvqVYrtWJ"
                target="_blank"
                rel="noopener noreferrer"
                aria-label="JobStreet"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 32 32"
                  aria-hidden="true"
                >
                  <path
                    d="M5 16h14.5M15 7.5 23.5 16 15 24.5"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="4"
                    stroke-linecap="square"
                    stroke-linejoin="miter"
                  />
                </svg>
              </a>


            <a
              href="https://github.com/allyuh"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="GitHub"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                aria-hidden="true"
              >
                <path
                  d="M12 2C6.48 2 2 6.58 2 12.22c0 4.51 2.87 8.33 6.84 9.68.5.1.68-.22.68-.49v-1.7c-2.78.62-3.37-1.22-3.37-1.22-.45-1.18-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.06 1.53 1.06.9 1.57 2.36 1.12 2.94.86.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.14-4.56-5.05 0-1.12.39-2.03 1.02-2.75-.1-.26-.44-1.3.1-2.7 0 0 .84-.28 2.75 1.05A9.2 9.2 0 0 1 12 7.14c.85 0 1.7.12 2.5.35 1.91-1.33 2.75-1.05 2.75-1.05.54 1.4.2 2.44.1 2.7.63.72 1.02 1.63 1.02 2.75 0 3.92-2.35 4.78-4.59 5.04.36.32.68.94.68 1.9v2.82c0 .27.18.59.69.49A10.23 10.23 0 0 0 22 12.22C22 6.58 17.52 2 12 2Z"
                />
              </svg>
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
