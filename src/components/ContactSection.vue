<template>
  <section id="contact" class="contact-section">

    <div class="contact-content">

      <h2>Contact</h2>

      <div class="contact-buttons">

        <!-- fb -->
        <a
          href="https://www.facebook.com/fukamine.x"
          class="contact-button"
          target="_blank"
          rel="noopener noreferrer"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              d="M14 8h3V4h-3c-3.31 0-5 1.69-5 5v3H6v4h3v8h4v-8h3l1-4h-4V9c0-.67.33-1 1-1Z"
            />
          </svg>

          <span class="contact-main-text">Facebook</span>
          <span class="contact-hover-text">Allyanna Mejia</span>
        </a>


        <!-- gmail -->
        <button
          class="contact-button"
          type="button"
          @click="copyText('mejiaallya00@gmail.com', 'gmail')"
        >
          <svg
            v-if="copied !== 'gmail'"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              d="M3 6.5A2.5 2.5 0 0 1 5.5 4h13A2.5 2.5 0 0 1 21 6.5v11a2.5 2.5 0 0 1-2.5 2.5h-13A2.5 2.5 0 0 1 3 17.5v-11Z"
            />

            <path
              d="m4 6 8 6 8-6"
            />
          </svg>

          <span
            v-if="copied !== 'gmail'"
            class="contact-main-text"
          >
            Gmail
          </span>

          <span
            v-if="copied !== 'gmail'"
            class="contact-hover-text"
          >
            Click to copy
          </span>

          <span
            v-if="copied === 'gmail'"
            class="contact-copied-text"
          >
            Copied!
          </span>

          <span
            v-if="copied !== 'gmail'"
            class="contact-mobile-hint"
          >
            — Press to Copy
          </span>
        </button>


        <!-- phone no -->
        <button
          class="contact-button"
          type="button"
          @click="copyText('09204840767', 'phone')"
        >
          <svg
            v-if="copied !== 'phone'"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              d="M6.6 3.5 9 3l2 5-2.5 1.5a16 16 0 0 0 6.5 6.5L16.5 14l5 2 .5 2.4a2 2 0 0 1-2 2.6C11.7 21 3 12.3 3 4a2 2 0 0 1 2.6-2Z"
            />
          </svg>

          <span
            v-if="copied !== 'phone'"
            class="contact-main-text"
          >
            Contact Number
          </span>

          <span
            v-if="copied !== 'phone'"
            class="contact-hover-text"
          >
            Click to copy
          </span>

          <span
            v-if="copied === 'phone'"
            class="contact-copied-text"
          >
            Copied!
          </span>

          <span
            v-if="copied !== 'phone'"
            class="contact-mobile-hint"
          >
            — Press to Copy
          </span>

        </button>

      </div>

    <button
      class="back-to-top"
      type="button"
      @click="backToTop"
    >
      <span>Back to Top</span>

      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        aria-hidden="true"
      >
        <path d="M12 19V5" />
        <path d="M6 11l6-6 6 6" />
      </svg>
    </button>


    </div>


  </section>
</template>


<script setup>
import { ref } from 'vue'

const copied = ref(null)

const copyText = async (text, type) => {
  try {
    await navigator.clipboard.writeText(text)

    copied.value = type

    setTimeout(() => {
      copied.value = null
    }, 1500)

  } catch (error) {
    console.error('Failed to copy:', error)
  }
}
const backToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}
</script>
