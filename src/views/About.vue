<template>
  <div class="about">
    <div class="box-container">
      <div class="box personal">
        <h1>Persönliche Angaben</h1>
        <p>Name:<span>Marc Nicolas Baumann</span></p>
        <p>E-Mail:<span>marc.baumann@swisscom.com</span></p>
        <p>Geburtstag:<span>08.10.2002</span></p>
        <p>Nationalität / Heimatsort:<span>Schweiz / Krauchthal</span></p>
        <p>
          Ausbildung:<span
            >Informatiker Applikationsentwicklung<br />4. Lehrjahr</span
          >
        </p>
      </div>
      <div class="box hobbies">
        <h1>Hobbies</h1>
        <ul>
          <li>Zeichnen</li>
          <li>Musik</li>
          <li>Videospiele</li>
          <li>Filme und Serien</li>
        </ul>
      </div>
      <div class="box music">
        <h1>
          Musik
          <b-tooltip
            label="Bands und Sänger*innen, die aktuell höre"
            class="tooltip"
            ><b-icon class="h1-icon" icon="information-outline"></b-icon
          ></b-tooltip>
        </h1>
        <div class="scroll-container">
          <b-tooltip class="cover" label="Twenty One Pilots">
            <img src="@/assets/artists/Twenty One Pilots.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Imagine Dragons">
            <img src="@/assets/artists/Imagine Dragons.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Billie Eilish">
            <img src="@/assets/artists/Billie Eilish.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="AJR">
            <img src="@/assets/artists/AJR.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Queen">
            <img src="@/assets/artists/Queen.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Twenty One Pilots">
            <img src="@/assets/artists/Twenty One Pilots.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Imagine Dragons">
            <img src="@/assets/artists/Imagine Dragons.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Billie Eilish">
            <img src="@/assets/artists/Billie Eilish.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="AJR">
            <img src="@/assets/artists/AJR.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Queen">
            <img src="@/assets/artists/Queen.jpg" />
          </b-tooltip>
        </div>
        <div class="scroll-container lower">
          <b-tooltip class="cover" label="Woodkid">
            <img src="@/assets/artists/Woodkid.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Sia">
            <img src="@/assets/artists/Sia.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Adele">
            <img src="@/assets/artists/Adele.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Aurora">
            <img src="@/assets/artists/Aurora.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Eminem">
            <img src="@/assets/artists/Eminem.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Woodkid">
            <img src="@/assets/artists/Woodkid.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Sia">
            <img src="@/assets/artists/Sia.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Adele">
            <img src="@/assets/artists/Adele.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Aurora">
            <img src="@/assets/artists/Aurora.jpg" />
          </b-tooltip>
          <b-tooltip class="cover" label="Eminem">
            <img src="@/assets/artists/Eminem.jpg" />
          </b-tooltip>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {};
  },
  components: {},
  created() {},
  methods: {},
};
</script>

<style lang="scss">
@function random_range($min, $max) {
  $rand: random();
  $random_range: $min + $rand * (($max - $min) + 1);
  @return random_range;
}

$cover-size: 80px;
$cover-gap: 16px;

.box-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 48px;
}
.box {
  padding: 24px;
  background: #242729;
  color: white;
  border-radius: 30% 50% 20% 40%;
  animation: transform 20s ease-in-out infinite both alternate;
  box-shadow: 11px 10px 38px hsla(0, 0%, 0%, 38%);
  line-height: 32px;
  margin: auto;
  overflow: hidden;

  .tooltip {
    position: absolute;
    margin-left: 10px;
    font-family: "Rubik", sans-serif;
    text-transform: none;
  }

  img {
    height: 80px;
    width: 80px;
    background: #242729;

    border-radius: 30% 50% 20% 40%;
    animation: transform 20s ease-in-out infinite both alternate;
    //border-radius: 10px;
  }

  h1 {
    text-align: center;
    color: white;
    font-size: 24px;
    font-weight: bold;
    font-family: "Arvo", serif;
    text-transform: uppercase;
    margin: 16px 0;

    .h1-icon {
      opacity: 0.5;
    }
  }

  .scroll-container {
    position: relative;
    width: 1000px;
    overflow: show;
    display: flex;
    gap: $cover-gap;

    &.lower {
      margin-left: -$cover-size / 2 - $cover-gap / 2;
    }

    .cover {
      animation: slide 30s linear infinite;

      /*       &:nth-child(1) {
        left: 0px;
      }
      &:nth-child(2) {
        left: $cover-size / 2 + $cover-gap;
        top: $cover-size + $cover-gap;
      }
      &:nth-child(3) {
        left: $cover-size + $cover-gap * 2;
      }
      &:nth-child(4) {
        left: $cover-size * 2 + $cover-gap;
        top: $cover-size + $cover-gap;
      }
      &:nth-child(5) {
        left: $cover-size * 2 + $cover-gap * 4;
      } */
    }
  }
}

.music {
  width: 300px;
}

.hobbies {
  padding: 24px 64px 64px 64px;
}

.personal {
  width: 600px;
  padding: 24px 64px 64px 64px;

  p {
    font-weight: bold;
  }

  span {
    font-weight: normal;
    float: right;
    text-align: right;
  }
}

@keyframes slide {
  0% {
    transform: translate3d(0, 0, 0);
  }
  100% {
    transform: translate3d(-482px, 0, 0); /* The image width */
  }
}
</style>