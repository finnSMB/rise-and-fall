<template>
  <div class="home">
    <div class="home-text">
      <p>Welcome. A new civilisation is about to be created..</p>
    </div>
    <div v-if="isEvent" class="home-events">
      <!-- replace with v-for -->
      <button>Event response 1</button>
      <button>Event response 2</button>
      <button>Event response 3</button>
      <button>Event response 4</button>
    </div>
    <Debug :hasEvent="isEvent" @event-spawn="isEvent = !isEvent" @text-spawn="addToTextBox" />
  </div>
</template>

<script>
import Debug from "@/components/Debug.vue"
export default {
  name: 'HomeView',
  components: {
    Debug,
  },
  data() {
    return {
      isEvent: false
    }
  },
  props: {},
  methods: {
    addToTextBox(text) {
      const textBox = document.getElementsByClassName("home-text")[0]
      const newText = document.createElement("p")
      newText.innerText = text
      newText.classList.add("event")
      textBox.append(newText)
      this.updateScroll()
    },
    updateScroll() {
      var textBox = document.getElementsByClassName("home-text")[0]
      textBox.scrollTop = textBox.scrollHeight
    }
  },
  created() {
    console.log(1)
  },
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
  max-height: 320px;
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
