<template>
  <div class="section">
    <div class="mountain-container">
      <!-- 背景層 -->
      <div class="background parallax-layer"></div>
      
      <!-- 霧氣層 -->
      <div class="fog-6 parallax-layer"></div>
      
      <!-- 低層山脈 -->
      <div class="mountain-low">
        <div class="fog-4 parallax-layer"></div>
        <div class="mountain-10 parallax-layer"></div>
        <div class="mountain-7 parallax-layer"></div>
        <div class="mountain-9 parallax-layer"></div>
      </div>
      
      <!-- 中層山脈 -->
      <div class="mountain-mid">
        <div class="fog-3 parallax-layer"></div>
        <div class="mountain-8 parallax-layer"></div>
        <div class="mountain-6 parallax-layer"></div>
        <div class="fog-7 parallax-layer"></div>
        <div class="fog-5 parallax-layer"></div>
        <div class="website-text parallax-layer">wedsite</div>
        <div class="mountain-5 parallax-layer"></div>
      </div>
      
      <!-- 高層山脈 -->
      <div class="mountain-high">
        <div class="mountain-3 parallax-layer"></div>
        <div class="mountain-1 parallax-layer"></div>
        <div class="mountain-4 parallax-layer"></div>
        <div class="fog-1 parallax-layer"></div>
        <div class="mountain-2 parallax-layer"></div>
        <div class="fog-2 parallax-layer"></div>
        <div class="modern-text parallax-layer">modern</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted } from 'vue'
import parallaxConfig from '../config/parallax-config.json'

const handleMouseMove = (e) => {
  const centerX = window.innerWidth / 2
  const centerY = window.innerHeight / 2
  const mouseX = e.clientX - centerX
  const mouseY = e.clientY - centerY

  for (const layerKey in parallaxConfig) {
    const layer = parallaxConfig[layerKey]
    const layerMultiplier = layer.layerMultiplier

    for (const elementKey in layer.elements) {
      // Skip text elements
      if (elementKey === 'website_text' || elementKey === 'modern_text') {
        continue
      }

      const elementConfig = layer.elements[elementKey]
      // Use replace to handle keys like 'mountain_10' becoming 'mountain-10'
      const el = document.querySelector(`.${elementKey.replace(/_/g, '-')}`)
      
      if (el) {
        const { speedX, speedY } = elementConfig
        const x = (mouseX * speedX * layerMultiplier)
        const y = (mouseY * speedY * layerMultiplier)
        el.style.transform = `translateX(${x}px) translateY(${y}px)`
      }
    }
  }
}

onMounted(() => {
  for (const layerKey in parallaxConfig) {
    const layer = parallaxConfig[layerKey]
    for (const elementKey in layer.elements) {
      const elementConfig = layer.elements[elementKey]
      const el = document.querySelector(`.${elementKey.replace(/_/g, '-')}`)
      
      if (el) {
        el.style.left = `${elementConfig.originalX}px`
        el.style.top = `${elementConfig.originalY}px`
      }
    }
  }
  document.addEventListener('mousemove', handleMouseMove)
})

onUnmounted(() => {
  document.removeEventListener('mousemove', handleMouseMove)
})
</script>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.section {
    position: relative;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
}

.mountain-container {
    position: absolute;
    width: 3077px;
    height: 2000px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    overflow: hidden;
}

/* 背景層 */
.background {
    position: absolute;
    top: -1531px;
    left: -1199px;
    width: 5682px;
    height: 3650px;
    background-image: url('/img/background.png');
    background-size: cover;
    background-position: center;
    z-index: 1;
}

/* 霧氣層 */
.fog-6 {
    position: absolute;
    top: 1003px;
    left: -274px;
    width: 3635px;
    height: 1253px;
    background-image: url('/img/fog_6.png');
    background-size: cover;
    background-position: center;
    z-index: 2;
}

/* 低層山脈 */
.mountain-low {
    position: absolute;
    top: 70px;
    left: 0;
    width: 100%;
    height: 2000px;
    z-index: 3;
}

.fog-4 {
    position: absolute;
    top: 679px;
    left: 1174px;
    width: 1030px;
    height: 849px;
    background-image: url('/img/fog_4.png');
    background-size: cover;
    background-position: center;
}

.mountain-10 {
    position: absolute;
    top: 990px;
    left: 858px;
    width: 1837px;
    height: 1416px;
    background-image: url('/img/mountain_10.png');
    background-size: cover;
    background-position: center;
}

.mountain-7 {
    position: absolute;
    top: 611px;
    left: 1671px;
    width: 1237px;
    height: 1441px;
    background-image: url('/img/mountain_7.png');
    background-size: cover;
    background-position: center;
}

.mountain-9 {
    position: absolute;
    top: 439px;
    left: 204px;
    width: 1039px;
    height: 1700px;
    background-image: url('/img/mountain_9.png');
    background-size: cover;
    background-position: center;
}

/* 中層山脈 */
.mountain-mid {
    position: absolute;
    top: 70px;
    left: 0;
    width: 100%;
    height: 2000px;
    z-index: 4;
}

.fog-3 {
    position: absolute;
    top: 304px;
    left: 423px;
    width: 2755px;
    height: 1392px;
    background-image: url('/img/fog_3.png');
    background-size: cover;
    background-position: center;
}

.mountain-8 {
    position: absolute;
    top: 409px;
    left: 378px;
    width: 1768px;
    height: 1640px;
    background-image: url('/img/mountain_8.png');
    background-size: cover;
    background-position: center;
}

.mountain-6 {
    position: absolute;
    top: 160px;
    left: 2465px;
    width: 934px;
    height: 2071px;
    background-image: url('/img/mountain_6.png');
    background-size: cover;
    background-position: center;
}

.fog-7 {
    position: absolute;
    top: 409px;
    left: -288px;
    width: 3365px;
    height: 2236px;
    background-image: url('/img/fog_7.png');
    background-size: cover;
    background-position: center;
}

.fog-5 {
    position: absolute;
    top: 765px;
    left: 1176px;
    width: 819px;
    height: 827px;
    background-image: url('/img/fog_5.png');
    background-size: cover;
    background-position: center;
}

.website-text {
    position: absolute;
    top: 870px;
    left: 1294px;
    width: 853px;
    height: 288px;
    font-family: 'Inria Serif', serif;
    font-weight: 400;
    font-size: 240px;
    line-height: 1.199em;
    color: #FFFFFF;
    z-index: 5;
}

.mountain-5 {
    position: absolute;
    top: 978px;
    left: 1317px;
    width: 1301px;
    height: 1150px;
    background-image: url('/img/mountain_5.png');
    background-size: cover;
    background-position: center;
}

/* 高層山脈 */
.mountain-high {
    position: absolute;
    top: 70px;
    left: 0;
    width: 100%;
    height: 2000px;
    z-index: 6;
}

.mountain-3 {
    position: absolute;
    top: 710px;
    left: 2667px;
    width: 819px;
    height: 1478px;
    background-image: url('/img/mountain_3.png');
    background-size: cover;
    background-position: center;
}

.mountain-1 {
    position: absolute;
    top: 20px;
    left: -216px;
    width: 1258px;
    height: 2300px;
    background-image: url('/img/mountain_1.png');
    background-size: cover;
    background-position: center;
}

.mountain-4 {
    position: absolute;
    top: 799px;
    left: 22px;
    width: 1649px;
    height: 1300px;
    background-image: url('/img/mountain_4.png');
    background-size: cover;
    background-position: center;
}

.fog-1 {
    position: absolute;
    top: 838px;
    left: 700px;
    width: 2377px;
    height: 1158px;
    background-image: url('/img/fog_1.png');
    background-size: cover;
    background-position: center;
}

.mountain-2 {
    position: absolute;
    top: 592px;
    left: 1764px;
    width: 1566px;
    height: 1650px;
    background-image: url('/img/mountain_2.png');
    background-size: cover;
    background-position: center;
}

.fog-2 {
    position: absolute;
    top: 717px;
    left: -61px;
    width: 2728px;
    height: 1283px;
    background-image: url('/img/fog_2.png');
    background-size: cover;
    background-position: center;
}

.modern-text {
    position: absolute;
    top: 749px;
    left: 895px;
    width: 816px;
    height: 305px;
    font-family: 'Algerian', serif;
    font-weight: 400;
    font-size: 170px;
    line-height: 1.32em;
    color: #FFFFFF;
    z-index: 7;
}

/* 視差效果 */
.parallax-layer {
    transition: transform 0.1s ease-out;
}

/* 響應式設計 */
@media (max-width: 768px) {
    .website-text {
        font-size: 120px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .modern-text {
        font-size: 85px;
        top: 60%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
}
</style> 