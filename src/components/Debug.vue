<template>
  <div class="home-debug">
    Debug Items
    <button @click="spawn">Spawn Text</button>
    <button :value="isEvent" @click="this.$emit('event-spawn', isEvent)">isEvent: {{isEvent}}</button>
  </div>
</template>

<script>
export default {
  name: "Debug-item",
  data() {
    return {
      isEvent: this.hasEvent,
    }
  },
  props: {
    hasEvent: Boolean,
  },
  methods: {
    spawn() {
      const textBox = document.getElementsByClassName("home-text")[0]
      const newText = document.createElement("p")
      newText.innerText = "Hello!"
      newText.classList.add("event")
      textBox.append(newText)
      this.$emit('scroll-event', 1)
    }
  }
}
</script>

<style lang="scss" scoped>
.home-debug {
  width: 200px;
  display: flex;
  text-align: center;
  flex-direction: column;
  align-content: center;
  justify-content: center;
  background-color: blueviolet;
  padding: 5px;
}
</style>
