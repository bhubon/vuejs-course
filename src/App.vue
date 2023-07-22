<script setup>

import { ref, computed } from 'vue';

const images = [
    {
        thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
        full: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
        caption: 'Night in Desert'
    },
    {
        thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60",
        full: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
        caption: 'Day In Desert'
    },
    {
        thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
        full: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
        caption: 'Sky view in desert'
    },
    {
        thumb: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
        full: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d??ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
        caption: 'Mountain'
    }
]

let currentIndex = ref(0);
const imagesLength = images.length

const swithchSlider = (targer) => {

    if ('next' == targer) {
        currentIndex.value = (imagesLength - 1) > currentIndex.value ? currentIndex.value + 1 : 0;
    } else {
        currentIndex.value = currentIndex.value > 0 ? currentIndex.value - 1 : (imagesLength - 1);
    }
}

const swithchNa = (index) => {
    currentIndex.value = index
}

</script>

<template>
    <div class="slideshow-container">

        <!-- Full-width images with number and caption text -->
        <div class="mySlides">
            <div class="numbertext">{{ currentIndex + 1 }} / {{ imagesLength }}</div>
            <img :src="images[currentIndex].full" style="width:100%">
            <div class="text">{{ images[currentIndex].caption }}</div>
        </div>

        <!-- Next and previous buttons -->
        <a class="prev" @click="swithchSlider('prev')">&#10094;</a>
        <a class="next" @click="swithchSlider('next')">&#10095;</a>
    </div>
    <br>

    <!-- The dots/circles -->
    <div style="text-align:center">
        <span class="dot" v-for="(image, index) in images" :key="index" @click="swithchNa(index)"
            :style="{ backgroundImage: `url(${image.thumb})` }"></span>
    </div>
</template>

<style scoped>
* {
    box-sizing: border-box
}
body{
    background: #fff;
}

/* Slideshow container */
.slideshow-container {
    max-width: 1000px;
    position: relative;
    margin: auto;
}

/* Hide the images by default */


/* Next & previous buttons */
.prev,
.next {
    cursor: pointer;
    position: absolute;
    top: 50%;
    margin-top: -22px;
    color: white;
    font-weight: bold;
    font-size: 18px;
    transition: 0.6s ease;
    user-select: none;
    background: #1e90ff;
    line-height: 42px;
    height: 42px;
    width: 42px;
    border-radius: 50% !important;
}


/* Position the "next button" to the right */
.next {
    right: 0;
    border-radius: 3px 0 0 3px;
}

/* Position the "prev button" to the right */
.prev {
    left: 0;
    border-radius: 3px 0 0 3px;
}

/* On hover, add a black background color with a little bit see-through */


/* Caption text */
.text {
    color: #f2f2f2;
    font-size: 15px;
    padding: 8px 12px;
    position: absolute;
    bottom: 8px;
    width: 100%;
    text-align: center;
}

/* Number text (1/3 etc) */
.numbertext {
    color: #f2f2f2;
    font-size: 12px;
    padding: 8px 12px;
    position: absolute;
    top: 0;
}

/* The dots/bullets/indicators */
.dot {
    cursor: pointer;
    height: 50px;
    width: 50px;
    margin: 0 2px;
    background-color: #bbb;
    border-radius: 50%;
    display: inline-block;
    transition: background-color 0.6s ease;
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
}

.active,
.dot:hover {
    background-color: #717171;
}

img{
    height: 730px;
    object-fit: cover;
}

</style>
