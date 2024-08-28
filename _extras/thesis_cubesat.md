---
layout: page
title: Structural Design and Verification of Weight Reduction for 12U Cube Satellite
img: assets/img/publication_preview/Thesis_2020.gif
importance: 2
category: study
description: "[Undergraduate Thesis] We propose a lightweight 12U CubeSat structure that meets both stiffness and design requirements."
related_publications: true
images:
  slider: true
---

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true" style="width: 500px; height: 500px;">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/extra/cubesat_1.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/extra/cubesat_2.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/extra/cubesat_3.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>

<br/>
<br/>

## Overview 

The development of CubeSats has recently accelerated due to their cost-effectiveness compared to traditional satellites. To optimize the economic utilization of CubeSats, minimizing overall weight is essential, while also meeting critical constraints such as structural stiffness. In this project, we propose **a lightweight 12U CubeSat structure** that meets both stiffness and design requirements. To achieve this, we conducted structural analyses using ANSYS, verifying that the modal and random vibration analyses adhered to the standards outlined in `NASA-GSFC-STD-7000A`. As a result, we achieved a `34%` weight reduction compared to the original design, culminating in the successful fabrication of the final structure.


### Our 12U Cubesat Strucuture

<model-viewer ar auto-rotate src="/assets/project_material/cubesat.glb" poster="/assets/project_material/cubesat.webp" tone-mapping="neutral" shadow-intensity="1" camera-controls touch-action="pan-y" alt="A 3D model carousel" style="width: 600px; height: 600px;">
  
  <div class="slider">
    <div class="slides">
      <button class="slide selected" onclick="switchSrc(this, 'cubesat')" style="background-image: url('/assets/project_material/cubesat.webp');">
      </button><button class="slide" onclick="switchSrc(this, 'cubesat_front')" style="background-image: url('/assets/project_material/cubesat_front.webp');">
      </button><button class="slide" onclick="switchSrc(this, 'cubesat_side')" style="background-image: url('/assets/project_material/cubesat_side.webp');">
      </button><button class="slide" onclick="switchSrc(this, 'cubesat_top')" style="background-image: url('/assets/project_material/cubesat_top.webp');">
      </button>
    </div>
  </div>
</model-viewer>

<br/>
<br/>



- This project was carried out over the course of a year in collaboration with [NARA SPACE](https://www.naraspace.com/) and contributed to the development of [BUSANSAT-A](http://www.bsnewocean.or.kr/bbs/content.php?co_id=sat#). 
- Additionally, our team received third place among over 90+ teams in the 2020 PNU CAPSTONE DESIGN Poster session {% cite ahn20thesis_cubesat %}.

<br/>
<br/>
<br/>
<br/>

<script type="module">
  const modelViewer = document.querySelector("model-viewer");

  window.switchSrc = (element, name) => {
    const base = "/assets/project_material/" + name;
    modelViewer.src = base + '.glb';
    modelViewer.poster = base + '.webp';
    const slides = document.querySelectorAll(".slide");
    slides.forEach((element) => {element.classList.remove("selected");});
    element.classList.add("selected");
  };

  document.querySelector(".slider").addEventListener('beforexrselect', (ev) => {
    // Keep slider interactions from affecting the XR scene.
    ev.preventDefault();
  });
</script>
<style>
  /* This keeps child nodes hidden while the element loads */
  :not(:defined) > * {
    display: none;
  }

  model-viewer {
    background-color: #eee;
    overflow-x: hidden;
  }

  @keyframes circle {
    from { transform: translateX(-50%) rotate(0deg) translateX(50px) rotate(0deg); }
    to   { transform: translateX(-50%) rotate(360deg) translateX(50px) rotate(-360deg); }
  }

  @keyframes elongate {
    from { transform: translateX(100px); }
    to   { transform: translateX(-100px); }
  }

  .slider {
    width: 100%;
    text-align: center;
    overflow: hidden;
    position: absolute;
    bottom: 16px;
  }

  .slides {
    display: flex;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    -webkit-overflow-scrolling: touch;
  }

  .slide {
    scroll-snap-align: start;
    flex-shrink: 0;
    width: 100px;
    height: 100px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    background-color: #fff;
    margin-right: 10px;
    border-radius: 10px;
    border: none;
    display: flex;
  }

  .slide.selected {
    border: 2px solid #4285f4;
  }

  .slide:focus {
    outline: none;
  }

  .slide:focus-visible {
    outline: 1px solid #4285f4;
  }
</style>
