<template>
  <div class="about">
    <h1>This is an about page</h1>
    <canvas id="canvas"></canvas>
  </div>
</template>

<script>
export default {
  name: 'Player',
  components: {
  },
  mounted() {
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');

    ctx.fillStyle = 'green';
    ctx.fillRect(10, 10, 150, 100);
  },
};
</script>
