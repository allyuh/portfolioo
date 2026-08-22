<script setup>
import { ref } from 'vue'

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

</script>

<template>
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

          <h3>
            {{ projects[currentProject].name }}
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
