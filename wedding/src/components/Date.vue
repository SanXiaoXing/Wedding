<template>
    <div class="anniversary-container">
      <TypedText :texts="['今天的日期是 ' + currentDate ,'同时也是💍结婚纪念 ' + years + ' 周年💍, ❤第 ' + days + ' 天 ❤']" :typingSpeed="200"></TypedText>
    </div>
  </template>
  
  <style scoped>
  .anniversary-container {
    position: absolute;
    /* background-color: rgba(255, 255, 255, 0.5);
    backdrop-filter: blur(10px);
    border-radius: 20px; 设置圆角 */
    padding: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    left: 50%;
    transform: translate(-50%, -50%);
    font-family: 宋体;
    color: red;
  }
  </style>
  
  <script>
  import TypedText from '@/components/typedText.vue'

  export default {
    components: {
    TypedText
  },
    name: 'AnniversaryDate',
    data() {
      return {
        currentDate: '',
        years: 0,
        days: 0
      };
    },
    mounted() {
      this.calculateAnniversary();
    },
    methods: {
      calculateAnniversary() {
        // Set your anniversary date
        const anniversary = new Date('2023-10-02'); // Replace with your own anniversary date
  
        // Get the current date
        const today = new Date();
  
        // Calculate the difference in milliseconds between the two dates
        const timeDiff = Math.abs(today.getTime() - anniversary.getTime());
        
        // Calculate the number of days
        const days = Math.ceil(timeDiff / (1000 * 3600 * 24));
  
        // Calculate the number of years
        const years = Math.floor(days / 365);
        
        // Check if the anniversary date is in a leap year
        const anniversaryYear = anniversary.getFullYear();
        const isLeapYear = this.isLeapYear(anniversaryYear);
  
        // Adjust the number of days based on leap year or not
        if (isLeapYear && today > anniversary) {
          this.days = (days % 365) - 1;
        } else {
          this.days = days % 365;
        }
  
        // Update the data properties
        this.currentDate = today.toLocaleDateString();
        this.years = years;
      },
      isLeapYear(year) {
        return (year % 4 === 0 && year % 100 !== 0) || year % 400 === 0;
      }
    }
  };
  </script>