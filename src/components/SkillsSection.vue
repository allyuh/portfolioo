<script setup>
import { ref } from 'vue'

const showSkillMenu = ref(false)
const skillsAnimationKey = ref(0)
const selectedSkillCategory = ref('Skills')
const skillCategoryOptions = [
  'Skills',
  'IDE',
  'Hardware',
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

  Hardware: [
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
      'Project description placeholder.',
      'Project description placeholder.',
      'Project description placeholder.'
    ]
  },
  {
    name: 'ReeLiz',
    descriptions: [
      'Project description placeholder.',
      'Project description placeholder.',
      'Project description placeholder.'
    ]
  },
  {
    name: 'OGAE',
    descriptions: [
      'Project description placeholder.',
      'Project description placeholder.',
      'Project description placeholder.'
    ]
  },
  {
    name: 'DentaLiz',
    descriptions: [
      'Project description placeholder.',
      'Project description placeholder.',
      'Project description placeholder.'
    ]
  },
  {
    name: 'PotatoLiz',
    descriptions: [
      'Project description placeholder.',
      'Project description placeholder.',
      'Project description placeholder.'
    ]
  }
]

const currentProject = ref(0)

const nextProject = () => {
  if (currentProject.value < projects.length - 1) {
    currentProject.value++
  }
}

const previousProject = () => {
  if (currentProject.value > 0) {
    currentProject.value--
  }
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

      <h2 class="projects-heading">
        Projects
      </h2>


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
              v-for="description in projects[currentProject].descriptions"
              :key="description"
            >
              {{ description }}
            </li>
          </ul>

        </div>


        <!-- Right Arrow -->
        <button
          class="project-next"
          @click="nextProject"
          :disabled="currentProject === projects.length - 1"
          aria-label="Next project"
        >
          →
        </button>

      </div>


      <!-- Project Counter -->
      <div class="project-counter">
        {{ currentProject + 1 }} / {{ projects.length }}
      </div>


      <!-- Previous Arrow -->
      <button
        v-if="currentProject > 0"
        class="project-previous"
        @click="previousProject"
        aria-label="Previous project"
      >
        ←
      </button>

    </div>

  </section>
</template>
