<template>
  <div class="home-debug">
    Debug Items
    <button @click="this.$emit('text-spawn', 'Debug')">Spawn Text</button>
    <button :value="hasEvent" @click="this.$emit('event-spawn', hasEvent)">isEvent: {{hasEvent}}</button>
  </div>
</template>

<script>
export default {
  name: "Debug-item",
  props: {
    hasEvent: Boolean,
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
