<template>
    <div class="card" @mouseover="flipCard" @mouseleave="unflipCard">
      <div class="card-inner" :class="{ 'is-flipped': flipped }">
        <div class="card-front">
          <img src="../assets/Lover.svg" alt="Front Image">
        </div>
        <div class="card-back">
          <img src="../assets/720p.svg" alt="Back Image">
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CardComponent',
    data() {
      return {
        flipped: false
      };
    },
    methods: {
      flipCard() {
        this.flipped = true;
      },
      unflipCard() {
        this.flipped = false;
      }
    }
  };
  </script>
  
  <style>
  .card {
    width: 200px;
    height: 200px;
    perspective: 1000px;
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
  
  .card-front img,
  .card-back img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .card-front {
    background-color: transparent;
  }
  
  .card-back {
    background-color: transparent;
    transform: rotateY(180deg);
  }
  </style>