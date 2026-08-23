<script setup>
import { ref } from 'vue'

const showGallery = ref(false)
const selectedGallery = ref(0)
const currentGalleryImage = ref(0)
const showSkillMenu = ref(false)
const skillsAnimationKey = ref(0)
const selectedSkillCategory = ref('Skills')
const skillCategoryOptions = [
  'Skills',
  'IDE',
  'Hardware and Database',
  'Soft Skills'
]
const skillCategories = {
  Skills: [
    ['HTML', 'C#'],
    ['CSS', 'React'],
    ['JavaScript', 'React Native'],
    ['Java', '']
  ],

  IDE: [
    ['Visual Studio Code', 'Visual Studio'],
    ['Eclipse', 'Notepad++'],
    ['Arduino IDE', 'XAMPP']
  ],

  'Hardware and Database': [
    ['Arduino UNO R3', 'SQL'],
    ['Sensors for Arduino']
  ],

  'Soft Skills': [
    ['Willingness to learn', 'Good time management'],
    ['Easy to adapt', 'Fluent in English'],
    ['Good communication skills', 'Fast learner']
  ]
}

const selectSkillCategory = (category) => {
  selectedSkillCategory.value = category
  showSkillMenu.value = false

  skillsAnimationKey.value++
}
const projects = [
  {
    name: 'NutriLiz',
    descriptions: [
      'Undergraduate Thesis (2025-2026)',
      'Kiosk and Mobile App for easier access to nutrition information',
      'Role: Mobile App Designer and Tester (React Native)'
    ]
  },
  {
    name: 'ReeLiz',
    descriptions: [
      'Cognate Project (2025)',
      'Movie Listing and Ticketing System ',
      'Role: Website Designer (Bootstrap, JS, CSS) '
    ]
  },
  {
    name: 'OGAE',
    descriptions: [
      'Cognate Project (2024)',
      'Arduino-Enabled Greenhouse Monitoring System',
      'Role: C++ Software Developer - Backend via Arduino IDE'
    ]
  },
  {
    name: 'DentaLiz',
    descriptions: [
      'Software Design Project (2024)',
      'Dashboard & Management System ',
      'Role: C# Software Developer UI Designer - Backend & Local hosting '
    ]
  },
  {
    name: 'PotatoLiz',
    descriptions: [
      'Advanced Programming Project (2024)',
      'Point of Sale (POS) System',
      'Role: Software Developer & UI Designer - Backend & Local hosting'
    ]
  }
]

const currentProject = ref(0)

const nextProject = () => {
  currentProject.value =
    (currentProject.value + 1) % projects.length
}

const previousProject = () => {
  currentProject.value =
    (currentProject.value - 1 + projects.length) % projects.length
}

const projectGallery = [
  {
    name: 'NutriLiz',
    images: [
      '/images/projects/nutriliz1.png',
      '/images/projects/nutriliz2.png'
    ]
  },

  {
    name: 'ReeLiz',
    images: [
      '/images/projects/reeliz1.png',
      '/images/projects/reeliz2.png'
    ]
  },

  {
    name: 'OGAE',
    images: [
      '/images/projects/ogae1.png',
      '/images/projects/ogae2.png'
    ]
  },

  {
    name: 'DentaLiz',
    images: [
      '/images/projects/dentaliz1.png',
      '/images/projects/dentaliz2.png'
    ]
  },

  {
    name: 'PotatoLiz',
    images: [
      '/images/projects/potatoliz1.png',
      '/images/projects/potatoliz2.png'
    ]
  }
]

const openGallery = () => {
  selectedGallery.value = currentProject.value
  currentGalleryImage.value = 0
  showGallery.value = true
}

const closeGallery = () => {
  showGallery.value = false
}

const selectGalleryProject = (index) => {
  selectedGallery.value = index
  currentGalleryImage.value = 0
}

const nextGalleryImage = () => {
  const images = projectGallery[selectedGallery.value].images

  currentGalleryImage.value =
    (currentGalleryImage.value + 1) % images.length
}

const previousGalleryImage = () => {
  const images = projectGallery[selectedGallery.value].images

  currentGalleryImage.value =
    (currentGalleryImage.value - 1 + images.length) % images.length
}

</script>

<template>
      <!-- ========================================
        PROJECT GALLERY
    ======================================== -->

    <div
      v-if="showGallery"
      class="gallery-overlay"
    >

      <!-- Exit Button -->

      <button
        class="gallery-close"
        type="button"
        aria-label="Close gallery"
        @click="closeGallery"
      >
        ×
      </button>


      <!-- Project Tabs -->

      <div class="gallery-tabs">

        <button
          v-for="(project, index) in projectGallery"
          :key="project.name"
          type="button"
          class="gallery-tab"
          :class="{
            active: selectedGallery === index
          }"
          @click="selectGalleryProject(index)"
        >
          {{ project.name }}
        </button>

      </div>


      <!-- Gallery -->

      <div class="gallery-view">

        <!-- Previous -->

        <button
          class="gallery-arrow gallery-previous"
          type="button"
          aria-label="Previous image"
          @click="previousGalleryImage"
        >
          ←
        </button>


        <!-- Image -->

        <div class="gallery-image-container">

          <img
            :src="projectGallery[selectedGallery].images[currentGalleryImage]"
            :alt="`${projectGallery[selectedGallery].name} project image ${currentGalleryImage + 1}`"
            class="gallery-image"
          />

        </div>


        <!-- Next -->

        <button
          class="gallery-arrow gallery-next"
          type="button"
          aria-label="Next image"
          @click="nextGalleryImage"
        >
          →
        </button>

      </div>


      <!-- Image Pagination -->

      <div class="gallery-pagination">

        <button
          v-for="(image, index) in projectGallery[selectedGallery].images"
          :key="image"
          type="button"
          class="gallery-dot"
          :class="{
            active: currentGalleryImage === index
          }"
          @click="currentGalleryImage = index"
          :aria-label="`View image ${index + 1}`"
        >
        </button>

      </div>

    </div>
  <section id="skills" class="skills-section">

    <!-- LEFT SIDE -->
    <div class="skills-content">

      <!-- Skills Dropdown -->
      <div class="skills-heading-wrapper">

      <button
        class="skills-heading"
        :class="{
          'long-category': selectedSkillCategory === 'Hardware and Database' ||
                          selectedSkillCategory === 'Soft Skills'
        }"
        @click="showSkillMenu = !showSkillMenu"
      >
        {{ selectedSkillCategory }}

        <span
          class="dropdown-arrow"
          :class="{ open: showSkillMenu }"
        >
          ›
        </span>
      </button>

        <!-- Dropright Menu -->
      <div
        v-if="showSkillMenu"
        class="skills-menu"
      >
        <button
          v-for="category in skillCategoryOptions"
          :key="category"
          v-show="category !== selectedSkillCategory"
          @click="selectSkillCategory(category)"
        >
          {{ category }}
        </button>
      </div>

      </div>


      <!-- Skills List -->
      <div class="skills-list"
        :key="skillsAnimationKey">


        <ul>
          <li
            v-for="(skill, index) in skillCategories[selectedSkillCategory]"
            :key="'left-' + index"
          >
            {{ skill[0] }}
          </li>
        </ul>

        <ul>
          <li
            v-for="(skill, index) in skillCategories[selectedSkillCategory]"
            :key="'right-' + index"
            v-show="skill[1]"
          >
            {{ skill[1] }}
          </li>
        </ul>

      </div>

    </div>


    <!-- RIGHT SIDE -->
    <div class="projects-content">

    <div class="projects-title">
      <h2 class="projects-heading">
        Projects
      </h2>

      <div class="projects-line"></div>
    </div>


      <!-- Project Carousel -->
      <div class="project-carousel">

        <div
          class="project-card"
          :key="projects[currentProject].name"
        >

        <h3 class="project-title">
          <span>{{ projects[currentProject].name }}</span>

        <button
          class="project-view"
          type="button"
          aria-label="View project"
          @click="openGallery"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              d="M2.5 12s3.5-6 9.5-6 9.5 6 9.5 6-3.5 6-9.5 6-9.5-6-9.5-6Z"
            />
            <circle cx="12" cy="12" r="2.8" />
          </svg>
        </button>

        </h3>

          <ul>
            <li
              v-for="(description, index) in projects[currentProject].descriptions"
              :key="index"
            >
              {{ description }}
            </li>
          </ul>

        </div>


        <!-- Previous Arrow -->
        <button
          class="project-previous"
          @click="previousProject"
          aria-label="Previous project"
        >
          ←
        </button>

        <!-- Next Arrow -->
        <button
          class="project-next"
          @click="nextProject"
          aria-label="Next project"
        >
          →
        </button>

      </div>


      <!-- Pagination -->
      <div class="project-pagination">

        <button
          v-for="(project, index) in projects"
          :key="project.name"
          class="pagination-dot"
          :class="{ active: currentProject === index }"
          @click="currentProject = index"
          :aria-label="`Go to ${project.name}`"
        >
        </button>

      </div>


    </div>

  </section>
</template>
