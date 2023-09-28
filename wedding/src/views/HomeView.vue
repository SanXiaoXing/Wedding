<template>
  <div class="home">
  <div>
    <div class="card-container">
      <CardComponent
        :frontImage="require('../image/image6.jpg')"
        :backImage="require('../image/image5.jpg')"
        frontImageAlt="Front Image"
        backImageAlt="Back Image"
      ></CardComponent>
      <CardComponent
        :frontImage="require('../image/image23.jpg')"
        :backImage="require('../image/image22.jpg')"
        frontImageAlt="Front Image"
        backImageAlt="Back Image"
      ></CardComponent>
      <CardComponent
        :frontImage="require('../image/image27.jpg')"
        :backImage="require('../image/image26.jpg')"
        frontImageAlt="Front Image"
        backImageAlt="Back Image"
      ></CardComponent>
      <CardComponent
        :frontImage="require('../image/image15.jpg')"
        :backImage="require('../image/image14.jpg')"
        frontImageAlt="Front Image"
        backImageAlt="Back Image"
      ></CardComponent>
    </div>
  </div>
  </div>
</template>

<script>
import CardComponent from '@/components/Card.vue';

export default {
  name: 'HomeView',
  components: {
    CardComponent
  },
  mounted() {
    this.adjustContainerHeight();
    window.addEventListener('resize', this.adjustContainerHeight);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.adjustContainerHeight);
  },
  methods: {
    adjustContainerHeight() {
      const windowHeight = window.innerHeight;
      const cardContainer = document.querySelector('.card-container');
      if (cardContainer) {
        cardContainer.style.height = `${windowHeight * 0.8}px`;
      }
    }
  }
}
</script>
<style>
body {
  height: 100%;
  margin: 0;
  padding: 0;
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: center;
}

.home {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* 设置容器的高度为视口高度 */
  
}

.card-container {
  display: flex;
  justify-content: center;
  gap: 30px; /* 设置卡片之间的间距 */
  height: 80%; /* 设置卡片容器的高度为容器高度的80% */
  background-size: cover;
  background-position: center;
  background: #ffeaea;
  backdrop-filter: blur(10px); /* 使用高斯模糊效果 */
  border-radius: 50px; /* 设置圆角 */
  padding: 20px; /* 添加内边距来与背景图像形成间隔 */
}
</style>
