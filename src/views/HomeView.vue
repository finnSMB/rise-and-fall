<template>
  <div class="home">
    <div class="home-text">
      <p>Welcome. A new civilisation is about to be created..</p>
    </div>
    <div v-if="isEvent" class="home-events">
      home-events
    </div>
    <button @click="spawn">Spawn Text</button>
    <button :value="isEvent" @click="function() {isEvent = !isEvent}">isEvent: {{isEvent}}</button>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  components: {
  },
  data() {
    return {
      isEvent: false
    }
  },
  props: {},
  methods: {
    spawn() {
      const textBox = document.getElementsByClassName("home-text")[0]
      const newText = document.createElement("p")
      newText.innerText = "Hello!"
      newText.classList.add("event")
      textBox.append(newText)
      this.updateScroll()
    },
    updateScroll() {
      var textBox = document.getElementsByClassName("home-text")[0]
      textBox.scrollTop = textBox.scrollHeight
    }
  }
}
</script>

<style lang="scss">
@import "../scss/main.scss";

.home {
  padding: 10px $spacer;
}

.home > div {
  border-radius: 10px;
}

.home-text {
  margin: 5px 0;
  padding: 0 5px;
  max-height: 400px;
  overflow: auto;
}

.event {
  animation: append-animate .3s ease-in-out;
}

.home-events {
  margin: 5px 0;
  padding: 0 5px;
  color: blueviolet;
}
</style>
