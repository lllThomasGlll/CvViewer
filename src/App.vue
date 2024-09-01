<template>
  <div class="cv-container">
    <div class="cv-header">
      <img
        :src="currentPerson.image"
        alt="Profile Picture"
        class="profile-picture"
      />
      <div class="header-text">
        <h1>{{ currentPerson.name }}</h1>
        <h2>{{ currentPerson.profession }}</h2>
      </div>
    </div>

    <div class="cv-section">
      <h3>Sobre Mí</h3>
      <p>{{ currentPerson.bio }}</p>
    </div>

    <div class="cv-section">
      <h3>Experiencia</h3>
      <ul>
        <li v-for="(job, index) in currentPerson.experience" :key="index">
          <strong>{{ job.position }}</strong> en {{ job.companyName }} ({{
            job.timeExperience
          }})
        </li>
      </ul>
    </div>

    <div class="cv-section">
      <h3>Habilidades</h3>
      <ul class="skills">
        <li v-for="(skill, index) in currentPerson.skills" :key="index">
          {{ skill.Language }}
        </li>
      </ul>
    </div>

    <div class="cv-section">
      <h3>Contacto</h3>
      <p>Email: {{ currentPerson.contact.email }}</p>
      <p>Teléfono: {{ currentPerson.contact.number }}</p>
    </div>

    <button class="cv-button" @click="nextPerson">
      Siguiente ({{ index + 1 }}/{{ people.length }})
    </button>
  </div>
</template>

<script>
import { data } from "./data.js";

export default {
  data() {
    return {
      people: data,
      index: 0,
    };
  },
  computed: {
    currentPerson() {
      return this.people[this.index];
    },
  },
  methods: {
    nextPerson() {
      if (this.index < this.people.length - 1) {
        this.index++;
      } else {
        this.index = 0;
      }
    },
  },
};
</script>

<style scoped>
.cv-container {
  width: 800px;
  margin: 50px auto;
  font-family: "JetBrains Mono", monospace;
}

.cv-header {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.cv-header h1 {
  font-size: 36px;
}

.cv-header h2 {
  font-size: 24px;
  color: #777;
}

.profile-picture {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin-right: 20px;
}

.header-text {
  flex-grow: 1;
  text-align: left;
}

.cv-section {
  margin-bottom: 20px;
}

.cv-section h3 {
  font-size: 20px;
  border-bottom: 2px solid #333;
  margin-bottom: 10px;
  padding-bottom: 5px;
}

.cv-section p,
.cv-section ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

.skills {
  display: flex;
  flex-wrap: wrap;
}

.skills li {
  margin-right: 15px;
  padding: 5px 10px;
  border-radius: 5px;
}

.cv-button {
  margin: 50px auto;
  padding: 0 16px;
  width: 800px;
  height: 48px;

  background-color: #fcfcfd;
  border-radius: 4px;
  border: none;

  color: #36395a;
  box-shadow: rgba(45, 35, 66, 0.4) 0 2px 4px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;

  justify-content: center;
  align-items: center;
  font-size: 18px;

  text-decoration: none;
  text-align: center;

  transition: box-shadow 0.15s, transform 0.15s;
  display: inline-flex;
  white-space: nowrap;
  cursor: pointer;
}

.cv-button:focus {
  box-shadow: #d6d6e7 0 0 0 1.5px inset, rgba(45, 35, 66, 0.4) 0 2px 4px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;
}

.cv-button:hover {
  box-shadow: rgba(45, 35, 66, 0.4) 0 4px 8px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #d6d6e7 0 -3px 0 inset;
  transform: translateY(-2px);
}

.cv-button:active {
  box-shadow: #d6d6e7 0 3px 7px inset;
  transform: translateY(2px);
}
</style>
