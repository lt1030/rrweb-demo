<template>
  <div class="player">
  </div>
</template>

<script>
import { Replayer } from 'rrweb';

export default {
  name: 'Player',
  components: {
  },
  mounted() {
    const res = localStorage.getItem('rrweb-db');
    console.log(res);
    if (res) {
      console.log('value');
      const events = JSON.parse(res);

      const replayer = new Replayer(events);
      replayer.play();
    }
  },
};
</script>
