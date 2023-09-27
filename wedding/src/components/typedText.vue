<template>
    <div>
      <p>
        <span class="typed-text">{{ typedText }}</span>
        <span class="cursor"></span>
      </p>
    </div>
  </template>
  
  <style>
  .typed-text {
    position: relative;
  }
  
  .cursor {
    position: absolute;
    display: inline-block;
    width: 2px;
    height: 1.2em;
    margin-left: 2px;
    background-color: black;
    animation: blink-animation 0.7s step-end infinite;
  }
  
  @keyframes blink-animation {
    0% { opacity: 0; }
    50% { opacity: 1; }
    100% { opacity: 0; }
  }
  </style>
  
  <script>
  export default {
    props: {
      texts: {
        type: Array,
        required: true
      },
      typingSpeed: {
        type: Number,
        default: 100
      }
    },
    data() {
      return {
        currentIndex: 0, // 当前逐字显示的文本索引
        currentText: '', // 当前逐字显示的文本
        typedText: '', // 逐字显示的文本
        showCursor: true // 是否显示光标
      };
    },
    mounted() {
      this.startTyping();
    },
    methods: {
      startTyping() {
        this.currentText = this.texts[this.currentIndex];
        this.currentIndex = (this.currentIndex + 1) % this.texts.length;
  
        // 先删除之前的内容
        this.deleteText(() => {
          // 然后显示新的文字内容
          this.showText();
        });
      },
      showText() {
        if (this.currentText === '') {
          // 所有文本已经显示完，重新开始逐字显示
          this.startTyping();
          return;
        }
  
        setTimeout(() => {
          this.typedText += this.currentText[0];
          this.currentText = this.currentText.slice(1);
          this.showText();
        }, this.typingSpeed);
      },
      deleteText(callback) {
        if (this.typedText === '') {
          callback();
          return;
        }
  
        setTimeout(() => {
          this.typedText = this.typedText.slice(0, -1);
          this.deleteText(callback);
        }, this.typingSpeed);
      }
    }
  };
  </script>