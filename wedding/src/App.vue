<template>
  <div id="app">
    <Datetime></Datetime>
    <nav>
      <router-link to="/">纪念相册</router-link> |
      <router-link to="/about">纪念日期</router-link>
    </nav>
    <router-view/>
    <div class="music-container" @click="toggleMusic">
      <img :class="{'music-icon': true, 'rotate': isMusicPlaying}" src="../src/assets/music.svg" alt="音乐播放">
    </div>
    <audio ref="audio">
      <source src="../src/song/Ruu's Melody.mp3" type="audio/mpeg">
    </audio>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #f299a8;
}

.music-container {
  position: absolute;
  top: 20px;
  right: 20px;
  cursor: pointer;
}

.music-icon {
  width: 40px;
  height: 40px;
  transition: transform 0.5s ease; /* 添加过渡效果 */
}

.rotate {
  transform: rotate(360deg); /* 添加旋转样式 */
}
</style>


<script>
import Datetime from '@/components/Date.vue';
  

export default {
  components: {
    Datetime
  },
  data() {
    return {
      isMusicPlaying: true
    };
  },
  mounted() {
      const script = document.createElement('script');
      script.src = 'https://cdn.jsdelivr.net/gh/Fuukei/Public_Repository@latest/static/js/sakura-less.js';//添加樱花飘落样式
      document.body.appendChild(script);
      this.$refs.audio.play(); // 默认播放音乐
  },
  methods: {
    toggleMusic() {
      const audio = this.$refs.audio;
      const musicIcon = document.querySelector('.music-icon');
      if (audio.paused) {
        audio.play();
        this.isMusicPlaying = true;
        musicIcon.classList.add('rotate'); // 添加旋转样式类
      } else {
        audio.pause();
        this.isMusicPlaying = false;
        musicIcon.classList.remove('rotate'); // 移除旋转样式类
      }
    }
  }
}
</script>