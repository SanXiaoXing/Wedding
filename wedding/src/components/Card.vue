<template>
  <div class="card" @mouseenter="zoomInCard" @mouseleave="zoomOutCard" @click="toggleCardFlip" :style="{ transform: cardTransform }">
    <div class="card-inner" :class="{ 'is-flipped': flipped }">
      <div class="card-front">
        <img :src="frontImage" :alt="frontImageAlt" @click="triggerSinkEffect">
      </div>
      <div class="card-back">
        <img :src="backImage" :alt="backImageAlt">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    frontImage: {
      type: String,
      required: true
    },
    frontImageAlt: {
      type: String,
      default: 'Front Image'
    },
    backImage: {
      type: String,
      required: true
    },
    backImageAlt: {
      type: String,
      default: 'Back Image'
    }
  },
  data() {
    return {
      flipped: false,
      cardTransform: 'scale(1)' // Initial scale
    };
  },
  methods: {
    toggleCardFlip() {
      this.flipped = !this.flipped; // Toggle the flipped state
    },
    zoomInCard() {
      this.cardTransform = 'scale(1.05)'; // Scale up the card on mouseenter
    },
    zoomOutCard() {
      this.cardTransform = 'scale(1)'; // Reset the card scale on mouseleave
    },
    triggerSinkEffect(event) {
      const imgElement = event.target;
      imgElement.classList.add('sink');

      setTimeout(() => {
        imgElement.classList.remove('sink');
      }, 200); // Adjust the duration as needed
    }
  }
};
</script>

<style>
.card {
  width: 350px;
  height: 350px;
  perspective: 1000px;
  transition: transform 0.5s;
}

.card:hover {
  transform: scale(1.05); /* Scale up the card on hover */
}

.card-inner {
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 0.5s;
}

.card-inner.is-flipped {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

.card-front img {
  width: 350px;
  height: auto;
  object-fit: contain;
  border-radius: 10%;
  transition: transform 0.5s;
}

.card-front img.sink {
  transform: scale(0.95); /* Scale down the image when clicked */
}

.card-back img {
  width: 350px;
  height: auto;
  object-fit: contain;
  border-radius: 10%;
}

.card-front {
  background-color: transparent;
  border-radius: 20px;
}

.card-back {
  background-color: transparent;
  transform: rotateY(180deg);
  border-radius: 20px;
}
</style>