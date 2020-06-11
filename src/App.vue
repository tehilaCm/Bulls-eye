<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view /> -->
    <div class="container">
      <button class="prev" @click="plusDivs(-1)"><i class="material-icons">arrow_back</i></button>
      <div class="slider">
        <img :src="require('@/assets/13.png')" class="mySlides fade">
        <img :src="require('@/assets/14.png')" class="mySlides fade">
        <img :src="require('@/assets/6.png')" class="mySlides fade">
        <img :src="require('@/assets/1.png')" class="mySlides fade">
        <img :src="require('@/assets/5.png')" class="mySlides fade">
        <img :src="require('@/assets/15.png')" class="mySlides fade">
        <img :src="require('@/assets/1.png')" class="mySlides fade">
        <img :src="require('@/assets/8.png')" class="mySlides fade">
        <img :src="require('@/assets/1.png')" class="mySlides fade">
        <img :src="require('@/assets/3.png')" class="mySlides fade">
        <img :src="require('@/assets/2.png')" class="mySlides fade">
        <img :src="require('@/assets/4.png')" class="mySlides fade">
        <img :src="require('@/assets/7.png')" class="mySlides fade">
        <img :src="require('@/assets/9.png')" class="mySlides fade">
        <img :src="require('@/assets/10.png')" class="mySlides fade">
        <img :src="require('@/assets/11.png')" class="mySlides fade">
        <img :src="require('@/assets/12.png')" class="mySlides fade">
      </div>
      <button class="next" @click="plusDivs(1)"><i class="material-icons">arrow_forward</i></button>
    </div>
    
  </div>
</template>

<script>
export default {
  data(){
    return{
      slideIndex: 1
    }
  },
  methods:{
      plusDivs: function(n) {
      this.showDivs(this.slideIndex += n);
    },
     showDivs: function(n) {
      let i;
      let x = document.getElementsByClassName("mySlides");
      if (n > x.length) {this.slideIndex = 1}
      if (n < 1) {this.slideIndex = x.length}
      for (i = 0; i < x.length; i++) {
        x[i].style.display = "none";  
      }
      x[this.slideIndex-1].style.display = "block";  
    }
  },
  mounted(){
    this.showDivs(this.slideIndex);
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: calc(100vh);
  position: relative;
  overflow: hidden;
}

#app::after{
  overflow: hidden;
  position: absolute;
  content: "";
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  z-index:-99;
  background-image: url("assets/icon.jpg");
  background-position: center;
  background-size: cover;
  opacity: 0.1;
}

.container{
  height: 100vh;
  display: flex;
  justify-content: center;
}

.slider{
  width: 100%;
  background-image: none;
}

img{
  width:100%;
  height: 100%;
}

button{
  height: 2.5rem;
  width: 2.5rem;
  margin: 18rem 0rem;
  border-radius: 50%;
  border: none;
  color: white;
  background-color: #f785f3a1;
  cursor: pointer;
  position: absolute;
  z-index: 1;
}

.prev{
  animation: none;
  left: 0;
}

.next{
  animation: none;
  right: 0;
}

.fade {
  -webkit-animation-name: fade;
  -webkit-animation-duration: 1.5s;
  animation-name: fade;
  animation-duration: 1.5s;
}

@keyframes slidingRight {
  0%, 100% {
    transform: translate(0, 0);
  }
  
  50% {
    transform: translate(20px, 0)
  }
}

@keyframes slidingLeft {
  0%, 100% {
    transform: translate(0, 0);
  }
  
  50% {
    transform: translate(-20px, 0)
  }
}

@-webkit-keyframes fade {
  from {opacity: .4} 
  to {opacity: 1}
}

@keyframes fade {
  from {opacity: .4} 
  to {opacity: 1}
}

@media(min-width: 29rem)
{
  .slider{
    background-image: url('assets/smartphone.png');
    background-position: center;
    background-size: cover;
    width: 19rem;
    padding: 4rem 0.8rem;
  }
  .prev{
    animation: slidingLeft 2s linear infinite alternate;
  }

  .next{
    animation: slidingRight 2s linear infinite alternate;
  }

  button{
    height: 3rem;
    width: 3rem;
    margin: 18rem 0.5rem;
    position: inherit;
    background-color: #f785f3;
  }
}

</style>
