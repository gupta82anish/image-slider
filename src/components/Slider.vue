<template>
<div>
    <transition-group :name="slideDirection" tag='div' class="img-slider" id="slider">
      <div v-for="i in [currentIndex]" :key='i'>
        <img :src="currentImg.url" />
      </div>
    </transition-group>
    <label>{{currentImg.caption}}</label>
    <a class="prev" @click="prev" href='#'>&#10094;</a>
    <a class="next" @click="next" href='#'>&#10095;</a>
    <a class="next-down" @click="nextDown" href='#'>&#10095;</a>
    <a class="prev-up" @click="prevUp" href='#'>&#10095;</a>
</div>
</template>

<script>
import json from '../../static/data.json';
export default {
  name: 'Slider',
  data() {
    return {
      // images: [
      //   'https://cdn.pixabay.com/photo/2015/12/12/15/24/amsterdam-1089646_1280.jpg',
      //   'https://cdn.pixabay.com/photo/2016/02/17/23/03/usa-1206240_1280.jpg',
      //   'https://cdn.pixabay.com/photo/2015/05/15/14/27/eiffel-tower-768501_1280.jpg',
      //   'https://cdn.pixabay.com/photo/2016/12/04/19/30/berlin-cathedral-1882397_1280.jpg'
      //   ],
      timer: null,
      currentIndex: 0,
      slideDirection: null,
      images: json.data
    }
  },

  
    mounted: function() {
      // this.startSlide();
      console.log(this.myJson)
    },
  
    methods: {
      startSlide: function() {
        this.timer = setInterval(this.next, 4000);
      },
  
  
      next: function() {
        this.slideDirection = 'slide-left';
        this.currentIndex += 1
      },
      prev: function() {
        this.slideDirection = 'slide-right';
        this.currentIndex -= 1
        // document.getElementById("slider").style.transform = 'translate(-100%, 0)'
      },
      nextDown: function() {
        this.currentIndex +=1
        this.slideDirection = 'slide-up'
        // document.getElementById("slider").setAttribute("enter-active-class", "slide-next-down")
      },
      prevUp: function() {
        this.currentIndex -=1
        this.slideDirection = 'slide-down'
        // document.getElementById("slider").setAttribute("leave-to-class", "slide-prev-up")
      }
    },
  
    computed: {
      currentImg: function() {
        return this.images[Math.abs(this.currentIndex) % this.images.length];
      }
    }
  
}
</script>

<style>
.slide-left-enter-active,
.slide-left-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  position: absolute;
  width:100%;
  visibility: visible;
  opacity: 1;
}

.slide-right-enter-active,
.slide-right-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  position: absolute;
  width:100%;
  visibility: visible;
  opacity: 1;
}
.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  position: absolute;
  width:100%;
  visibility: visible;
  opacity: 1;
}


.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  position: absolute;
  width:100%;
  visibility: visible;
  opacity: 1;
}

.slide-left-enter {
  transform: translateX(100%);
}

.slide-left-leave-to {
  transform: translateX(-100%);
}

.slide-right-enter {
  transform: translateX(-100%);
}

.slide-right-leave-to {
  transform: translateX(100%);
}

.slide-up-enter {
  transform: translateY(100%);
}

.slide-up-leave-to {
  transform: translateY(-100%);
}

.slide-down-enter {
  transform: translateY(-100%);
}

.slide-down-leave-to {
  transform: translateY(100%);
}


img {
  height:250px;
  width:50%;
}

.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
}

/* Position the "next button" to the right */
.next {
  right: 0;
}

.next-down {
  cursor: pointer;
  position: absolute;
  left: 50%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
  bottom: 0px;
  transform: rotate(90deg)
}

.prev-up {
  cursor: pointer;
  position: absolute;
  top: 0px;
  left: 50%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
  /* bottom: 0px; */
  transform: rotate(-90deg)
}


.prev {
  left: 0;
}

/* On hover, add a black background color with a little bit see-through */
.prev:hover, .next:hover, .next-down:hover, .prev-up:hover {
  background-color: rgba(0,0,0,0.9);
}
</style>
