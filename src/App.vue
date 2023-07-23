<script setup>
import {ref} from "vue"
let mainImage = ref("../public/images/image-1.jpg")
let activeIndex = ref(1)
const images = [
  {
      id:1,
      src: '../public/images/image-1.jpg',
      alt: 'image one',
      isActive : true, 
    },
  {
      id: 2,
      src: '../public/images/image-2.jpg',
      alt: 'image one',
      isActive: false,   
    },
  {
      id: 3,
      src: '../public/images/image-3.jpg',
      alt: 'image one',
      isActive: false,    
    },
  {
      id: 4,
      src: '../public/images/image-4.jpg',
      alt: 'image one',
      isActive: false,       
    },
  {
      id: 5,
      src: '../public/images/image-5.jpg',
      alt: 'image one',
      isActive: false,      
    },
]



function changeSlider(image) {
  mainImage.value = image.src
  activeIndex = image.id
}

function nextImage(id){
  images.filter(function (element) {
    if (element.id == id) {
      changeSlider(element)
       
      }
    })
  }
function prevImage(id){
  images.filter(function (element) {
    if (element.id == id) {
       changeSlider(element)
      }
    })
}


setInterval(function () {

  nextImage(id+1)
}, 1000);

  




  
</script>

<template>
  <div class="container">
    <div class="mt-5  d-flex justify-content-center align-items-center">
      <div class="">
          <div  @click="changeSlider(image)" class="image-item" v-for="(image, index) in images" :key="index" >
            <img :class="image.id == activeIndex ? 'border-blue': ''" v-bind="image">
          </div>
      </div>
      <div>
        
        <img id="mainImage" class="mainImage img-fluid" :src="mainImage"/>
        <div class="arrow-group-container">
          <div class=" arrow-group d-flex justify-content-between">
            <div @click=" activeIndex == 1 ? activeIndex = images.length : activeIndex =  activeIndex -1; prevImage(activeIndex) " class="arrow-prev arrow">
                <i class="fa-solid fa-chevron-left"></i>
             </div>
            <div @click=" activeIndex != images.length ? activeIndex = activeIndex + 1 : activeIndex =1; nextImage(activeIndex)" class="arrow-next arrow">
              <i class="fa-solid fa-chevron-right"></i>
            </div>
          
          </div>
        </div>
        <div class="navigator d-flex justify-content-center">
            <div @click="changeSlider(image)" class="navigator-item " v-for="(image, index) in images" :key="index" > 
                <svg :fill="activeIndex == image.id ? '#ed3232' : '#ed32327a' " version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" 
                  width="50px" height="28px" viewBox="0 0 485.064 485.064"
                  xml:space="preserve">
                  <g>
                    <g>
                      <path d="M458.736,181.097H26.334C11.793,181.097,0,192.884,0,207.425v70.215c0,14.541,11.787,26.328,26.334,26.328h432.402
                    c14.541,0,26.328-11.787,26.328-26.328v-70.215C485.07,192.884,473.283,181.097,458.736,181.097z"/>
                    </g>
                  </g>
              </svg>
            </div>
          </div>
      </div>
    </div>
   
      
    
  </div>
</template>

<style scoped>
.image-item{
  width: 3rem;
  height: 3rem;
  margin: .5rem;
  
}
.image-item img{
  width: 100%;
  height: 100%;
  border-radius: 50px;
  cursor: pointer;
 
}
#mainImage{
  border-radius: 10px;
  min-height: 40rem;
  min-width: 60rem;
  max-height: 40rem;
  max-width: 60rem;
  position: relative;

}
.navigator-item{
  cursor: pointer;
}
.arrow-group-container{
  margin-right: 10px;
  margin-left: 10px;
  margin-top: 10px;
}
.arrow{
  cursor: pointer;

  
}
.arrow i{
  font-size: 20px;
}
.border-blue{
   border: 3px solid rgba(0, 94, 255, 0.94);
}
</style>
