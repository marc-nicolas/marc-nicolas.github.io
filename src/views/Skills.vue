<template>
  <div class="skills">
    <b-field>
      <b-input
        placeholder="Suche..."
        type="search"
        icon="magnify"
        v-model="search"
      >
      </b-input>
    </b-field>
    <div class="skill-group-header">
      <h1>Entwicklung</h1>

      <b-field>
        <b-select v-model="selectedSkillCategory">
          <option
            v-for="option in skillCategories"
            :value="option"
            :key="option"
          >
            {{ option }}
          </option>
        </b-select>
      </b-field>
    </div>
    <TransitionGroup name="list" class="skills-container">
      <div v-for="skill in skills" :key="skill.name">
        <div
          class="skill"
          v-if="
            (skill.type == selectedSkillCategory ||
              selectedSkillCategory == 'Alle') &&
            skill.displayName.toLowerCase().includes(search.toLowerCase())
          "
        >
          <b-tooltip :label="skill.displayName">
            <div>
              <img :src="getLogoPath(skill.name)" />
              <div class="skill-level-container">
                <div
                  class="bar"
                  v-bind:class="{ active: skill.level >= 1 }"
                ></div>
                <div
                  class="bar"
                  v-bind:class="{ active: skill.level >= 2 }"
                ></div>
                <div
                  class="bar"
                  v-bind:class="{ active: skill.level >= 3 }"
                ></div>
              </div>
            </div>
          </b-tooltip>
        </div>
      </div>
    </TransitionGroup>
    <div class="skill-group-header">
      <h1>Programme & Arbeitsmethoden</h1>

      <b-field>
        <b-select v-model="selectedProgramCategory">
          <option
            v-for="option in programCategories"
            :value="option"
            :key="option"
          >
            {{ option }}
          </option>
        </b-select>
      </b-field>
    </div>
    <TransitionGroup name="list" class="skills-container">
      <div v-for="skill in programs" :key="skill.name">
        <div
          class="skill"
          v-if="
            (skill.type == selectedProgramCategory ||
              selectedProgramCategory == 'Alle') &&
            skill.displayName.toLowerCase().includes(search.toLowerCase())
          "
        >
          <b-tooltip :label="skill.displayName">
            <div>
              <img :src="getLogoPath(skill.name)" />
              <div class="skill-level-container">
                <div
                  class="bar"
                  v-bind:class="{ active: skill.level >= 1 }"
                ></div>
                <div
                  class="bar"
                  v-bind:class="{ active: skill.level >= 2 }"
                ></div>
                <div
                  class="bar"
                  v-bind:class="{ active: skill.level >= 3 }"
                ></div>
              </div>
            </div>
          </b-tooltip>
        </div>
      </div>
    </TransitionGroup>
  </div>
</template>

<script>
import skillsJson from "@/data/skills.json";
import programsJson from "@/data/programs.json";

export default {
  name: "Home",
  data() {
    return {
      skills: skillsJson,
      programs: programsJson,
      skillCategories: [],
      selectedSkillCategory: "Alle",
      programCategories: [],
      selectedProgramCategory: "Alle",
      search: "",
    };
  },
  components: {},
  created() {
    this.skillCategories.push("Alle");
    this.skills.forEach((skill) => {
      if (!this.skillCategories.includes(skill.type))
        this.skillCategories.push(skill.type);
    });

    this.programCategories.push("Alle");
    this.programs.forEach((skill) => {
      if (!this.programCategories.includes(skill.type))
        this.programCategories.push(skill.type);
    });
  },
  methods: {
    getLogoPath(name) {
      try {
        return require("@/assets/logos/" + name + ".png");
      } catch {
        return require("@/assets/logos/html5.png");
      }
    },
  },
};
</script>

<style lang="scss">
$skill-height: 80px;
$skill-gap: 16px;

.skills {
  margin: auto;

  .input,
  select {
    background: #242729;
    color: white;
    border: none;

    &::placeholder {
      opacity: 0.5;
      color: white;
    }

    option {
      color: white;
      opacity: 0.5;
    }
  }

  .skill-group-header {
    text-align: center;
    display: flex;
    width: 100%;
    margin: 32px 0 24px 0;
    flex-direction: column;
    justify-content: space-between;

    h1 {
      color: white;
      font-size: 30px;
      font-family: "Arvo", serif;
      text-transform: uppercase;
      margin-top: auto;
      margin-bottom: 16px;
    }
  }
}

.skills-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  .skill {
    z-index: 100;
    position: relative;

    display: flex;
    flex-direction: row;
    height: $skill-height;
    width: $skill-height;
    background: #242729;

    border-radius: 30% 50% 20% 40%;
    animation: transform 20s ease-in-out infinite both alternate;
    //border-radius: 10px;
    box-shadow: 11px 10px 38px hsla(0, 0%, 0%, 38%);
    transition: 0.2s;
    margin: 0 $skill-gap $skill-gap 0;

    img {
      height: 48px;
      width: 48px;
      margin: 16px 16px 0 16px;
      //filter: drop-shadow(0px 0px 1px white);
    }

    &:hover {
      background: #888088;
      transform: scale(1.1);

      .skill-level-container {
        opacity: 1;
      }
    }

    .skill-level-container {
      opacity: 0;
      transition: 0.2s;

      position: absolute;
      height: 5px;
      width: 100%;
      display: flex;
      flex-direction: row;
      justify-content: center;
      gap: 4px;

      .bar {
        height: 5px;
        width: 5px;
        background: #434749;
        border-radius: 100px;
      }

      .active {
        background: #ffffff;
      }
    }
  }
}

.list-move, /* apply transition to moving elements */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
}

/* ensure leaving items are taken out of layout flow so that moving
   animations can be calculated correctly. */
.list-leave-active {
  position: absolute;
}
</style>