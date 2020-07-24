<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import { record } from 'rrweb';

let events = [];

export default {
  name: 'App',
  components: {
  },
  mounted() {
    localStorage.clear();

    record({
      emit(event) {
        // 将 event 存入 events 数组中
        events.push(event);
      },
    });

    // save 函数用于将 events 发送至后端存入，并重置 events 数组
    const save = () => {
      // const body = JSON.stringify({ events });
      // events = [];

      let db = localStorage.getItem('rrweb-db');
      if (db) {
        db = JSON.parse(db);
      } else {
        db = [];
      }
      db = db.concat(events);
      events = [];
      localStorage.setItem('rrweb-db', JSON.stringify(db));
      // fetch('http://YOUR_BACKEND_API', {
      //   method: 'POST',
      //   headers: {
      //     'Content-Type': 'application/json',
      //   },
      //   body,
      // });
    };

    // 每 10 秒调用一次 save 方法，避免请求过多
    setInterval(save, 3 * 1000);
    console.log('app');
  },
};
</script>

<style lang="scss">
body {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
