<template>
  <div class="contact">
    <h1>Melde dich bei mir!</h1>
    <p class="subtitle">
      Du kannst mich gerne auch direkt auf MS Teams anschreiben! :)
    </p>
    <div class="contact-container">
      <b-tooltip label="Mail">
        <a href="mailto:marc.baumann@swisscom.com">
          <div class="mail">
            <img src="@/assets/icons/mail.png" />
          </div>
        </a>
      </b-tooltip>
      <b-tooltip label="LinkedIn">
        <a
          href="https://www.linkedin.com/in/marc-baumann-801ab117b/"
          target="_blank"
        >
          <div class="linkedin"><img src="@/assets/icons/linkedin.png" /></div
        ></a>
      </b-tooltip>
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
$blob-height: 80px;
$blob-gap: 48px;

.contact {
  margin: auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  flex-direction: column;

  .subtitle {
    color: rgb(189, 189, 189);
    line-height: 60px;
    margin: 0;
    margin-bottom: 16px;
  }
  h1 {
    color: white;
    font-size: 30px;
    font-family: "Arvo", serif;
    text-transform: uppercase;
  }

  .contact-container {
    gap: $blob-gap;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-direction: row;
  }

  .mail,
  .linkedin {
    height: $blob-height;
    width: $blob-height;
    background: #d83327;
    border-radius: 30% 50% 20% 40%;
    animation: transform 20s ease-in-out infinite both alternate;
    transition: 0.2s;
    box-shadow: 11px 10px 38px hsla(0, 0%, 0%, 38%);

    img {
      height: 48px;
      width: 48px;
      margin: 16px 16px 0 16px;
    }

    &:hover {
      background: lighten(#d83327, 10%);
      transform: scale(1.1);
    }
  }

  .linkedin {
    background: #0077b5;
    &:hover {
      background: lighten(#0077b5, 10%);
    }
  }
}
</style>