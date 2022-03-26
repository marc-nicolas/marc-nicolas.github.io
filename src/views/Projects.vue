<template>
  <div class="projects">
    <h1>Persönliche Projekte</h1>
    <p class="subtitle">
      Hier findest du einige Projekte, an welchen ich privat gearbeitet habe.
    </p>
    <div class="list">
      <div v-for="project in projects" :key="project.name" class="project">
        <h1>{{ project.displayName }}</h1>
        <div class="description">
          <p v-html="project.description"></p>
          <a :href="project.url" target="_blank"
            ><b-button type="is-primary" outlined>Seite besuchen</b-button></a
          >
        </div>
        <b-carousel
          :autoplay="true"
          :overlay_x="galleryName == project.name"
          @click_x="switchGallery(true, project.name)"
          :indicator-inside="true"
          indicator-position="is-bottom"
          indicator-style="dots"
          :indicator-background="true"
          :pause-hover="true"
          :pause-info="false"
          :interval="5000"
        >
          <b-carousel-item
            v-for="(item, j) in getImages(project.name)"
            :key="j"
          >
            <a class="image">
              <img :src="getImages(project.name)[j]" />
            </a>
          </b-carousel-item>
          <span
            @click="switchGallery(false, project.name)"
            v-if="galleryName == project.name"
            class="modal-close is-large"
          />
        </b-carousel>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Projects",
  data() {
    return {
      galleryName: "",
      projects: [
        {
          name: "skribblist",
          displayName: "Skribblist",
          url: "https://baerliderfuchs.github.io/skribblist",
          description:
            'Vielleicht kennst du die Webseite <a href="https://skribbl.io/">Skribbl.io</a>, eine Online-Variante des Spiels "Montagsmaler". Eine Person zeichnet einen Begriff und die anderen müssen diesen erraten. Ein tolles Feature an dieser Webseite ist, dass man beim Spielen eigene Wörterlisten verwenden kann. Da meine Freunde und ich solche Wörterlisten oft verwenden habe ich Skribblist erstellt, eine Webseite, welche als Bibliothek mit diverse Wörterlisten dient. Die Webseite umfasst Wörterlisten aus verschiedensten Themengebieten, welche nach belieben kombiniert und für Skribbl.io verwendet werden können.',
        },
        {
          name: "jeoparody",
          displayName: "Jeoparody",
          url: "https://jeoparody.github.io",
          description:
            'In der Quizshow "Jeopardy!" geht es darum Fragen aus verschiedenen Kategorien zu beantworten, wobei ein höheres Preisgeld für schwierigere Fragen angeboten wird. Da ich dies mit meinen Freunden spielen wollte, erstellte ich "Jeoparody" - Eine Webseite rund um Quizshows. Die Webseite ermöglicht die Erstellung und das Spielen von eigenen Jeoparody-Spielbretten oder auch das Spielen von zufällig generierten Spielbretten mit Fragen aus einer API.<br>Neben Jeoparody gibt es aktuell einen weiteren Spielmodus "Trivia". Dabei handelt es sich um Multiple-Choice Quizfragen aus verschiedenen Themengebieten. Man kann seine Statistiken einsehen und seine Interessensgebiete angeben, um mehr Fragen aus dieser Kategorie zu erhalten.',
        },
        {
          name: "covidsim",
          displayName: "CovidSim",
          url: "https://covidsim.live",
          description:
            'Die Corona-Pandemie hat alle unsere Leben in den letzten paar Jahren auf den Kopf gestellt. Deswegen beschäftigten zwei Schulkollegen und ich uns mit dem Virus und den Faktoren und Massnahmen, welche den Verlauf der Pandemie beeinflussen. Dies war unser Thema für unsere IdPA (Abschlussarbeit der Berufsmaturitätsschule). Um den Einfluss der verschiedenen Faktoren auf die Pandemie zu messen erstellten wir "CovidSim". Mit diesem selbst erstellten Simulationsprogramm kann die Covid-19 Pandemie simuliert werden und live durch das Verändern der Faktoren wie Infektionsrate, Krankheitsdauer, Maskenpflicht, etc. beeinflusst werden.',
        },
      ],
    };
  },
  components: {},
  mounted() {},
  methods: {
    importAll(r, projectName) {
      let images = {};
      r.keys().map((item) => {
        if (item.includes(projectName))
          images[item.replace("./", "")] = r(item);
      });
      return images;
    },
    getImages(projectName) {
      return this.importAll(
        require.context("@/assets/projects/", true, /\.png$/),
        projectName
      );
    },
    switchGallery(value, galleryName) {
      console.log(this.galleryName);
      if (value) {
        this.galleryName = galleryName;
        document.documentElement.classList.add("is-clipped");
      } else {
        this.galleryName = "";
        document.documentElement.classList.remove("is-clipped");
      }
    },
  },
};
</script>

<style lang="scss">
$project-gap: 32px;
.projects {
  margin: auto;
  color: white;
  text-align: center;

  h1 {
    font-size: 42px;
    font-family: "Arvo", serif;
    text-transform: uppercase;
  }

  .subtitle {
    color: rgb(189, 189, 189);
    line-height: 60px;
  }
}

.list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: $project-gap;

  .project {
    position: relative;
    display: flex;
    flex-direction: column;
    width: 30%;
    min-width: 400px;
    background: #242729;
    border-radius: 10px;
    box-shadow: 11px 10px 38px hsla(0, 0%, 0%, 38%);
    transition: 0.2s;

    .description {
      position: absolute;
      background: #242729;
      text-align: justify;
      hyphens: auto;
      z-index: 100;
      height: 0;
      overflow: hidden;
      transition: 0.3s ease;
      bottom: 0;
      color: white;
      padding: 16px;
      padding-top: 0px;
      border-bottom-left-radius: 10px;
      border-bottom-right-radius: 10px;
      opacity: 0;

      p {
        height: calc(100% - 42px - 16px);
        overflow-y: scroll;
      }
      button {
        position: absolute;
        bottom: 16px;
        left: 50%;
        transform: translateX(-50%);
      }
    }

    img {
      border-bottom-left-radius: 10px;
      border-bottom-right-radius: 10px;
    }

    h1 {
      text-align: center;
      line-height: 40px;
      color: white;
      font-size: 20px;
    }

    &:hover {
      transform: scale(1.02);

      .description {
        opacity: 1;
        height: calc(100% - 39px);
        overflow: hidden;
      }
    }
  }
}
</style>