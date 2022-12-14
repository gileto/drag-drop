<script setup></script>

<template>
  <div class="main">
    <div class="container">
      <div class="drop"></div>
    </div>
  </div>
</template>

<script setup>
import interact from "interactjs";
const position = { x: 0, y: 0 };
interact(".drop").draggable({
  listeners: {
    move(event) {
      position.x += event.dx;
      position.y += event.dy;
      event.target.style.transform = `translate(${position.x}px, ${position.y}px)`;
    },
  },
  modifiers: [
    interact.modifiers.restrictRect({
      restriction: "parent",
    }),
  ],
});
</script>

<style scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.container {
  width: 80vw;
  height: 80vh;
  border-radius: 5px;
  background-color: burlywood;
  display: flex;
  justify-content: center;
  align-items: center;
}

.drop {
  width: 5rem;
  height: 5rem;
  background-color: beige;
  border-radius: 5px;
  cursor: move;
}
</style>
