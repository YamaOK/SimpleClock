<template>
  <body v-bind:style="`background:${this.backgroundColor}`">
    <header>{{ `${this.isVisible ? "Simple-Clock" : "&nbsp;"}` }}</header>
    <main v-bind:style="`background:${this.backgroundColor}`">
      <simple-clock></simple-clock>
    </main>
    <footer>
      <button v-on:click="this.turnLogoVisibility()">
        {{ `Logo ${this.isVisible ? "OFF" : "ON"}` }}
      </button>
      <div>
        <label class="colorPicker" for="colorPicker"
          >Change background Color</label
        >
        <input type="color" v-model="color" name="colorPicker" />
      </div>
      <a href="https://github.com/YamaOK" target="blank">@YamaOK/GitHub</a>
    </footer>
  </body>
</template>

<script>
import simpleClock from "./components/SimpleClock";
export default {
  name: "app",
  components: {
    simpleClock,
  },
  data: function () {
    return {
      logoVisible: true,
      color: "rgb(39, 34, 34)",
    };
  },
  methods: {
    turnLogoVisibility: function () {
      this.logoVisible = !this.logoVisible;
    },
  },
  computed: {
    isVisible: function () {
      return this.logoVisible;
    },
    backgroundColor: function () {
      return this.color;
    },
  },
};
</script>

<style scoped>
header {
  font-size: 3em;
  text-align: center;
  color: rgb(197, 197, 197);
  text-shadow: rgb(114, 114, 114) 2px 2px 2px, rgb(90, 90, 90) 3px 3px 3px,
    black 5px 5px 5px;
}
main {
  display: flex;
  height: 600px;
  width: 100%;
  flex-direction: column;
  justify-content: space-between;
  align-content: space-between;
  align-items: center;
}
footer {
  text-align: center;
  margin: 0 auto;
}
.colorPicker {
  font-size: 1.2em;
  color: rgb(197, 197, 197);
  text-shadow: rgb(114, 114, 114) 2px 2px 2px, rgb(90, 90, 90) 3px 3px 3px,
    black 5px 5px 5px;
  margin-right: 1em;
}
a {
  color: rgb(197, 197, 197);
  text-shadow: rgb(114, 114, 114) 2px 2px 2px, rgb(90, 90, 90) 3px 3px 3px,
    black 5px 5px 5px;
}
</style>
