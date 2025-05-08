<template>
  <Navbar />
  <div class="image-carousel-wrapper">
    <div class="image-carousel">
      <div class="image-carousel-slide">
        <img v-for="(image, index) in images" :src="image" alt="Profile Image" class="carousel-image" />
      </div>
      <div class="image-carousel-slide">
        <img v-for="(image, index) in images"  :src="image" alt="Profile Image" class="carousel-image" />
      </div>
    </div>
  </div>
  <section id="about-section">
    <div class="about-container">
      <h2>A Little About Me...</h2>
      <p>
        Hello! My name is Vivien, and my passion is making technology effortless to use, adopt, and maintain. I believe great design considers the people and their goals first—integrating naturally into real-world workflows and making life easier for users, developers, and stakeholders alike.
      </p>
      <p>
        Over the past few years, I’ve worked on full stack and front-end development, integrated AI into internal tools, and improved UX for platforms used by real-world teams. My technical toolbox includes Vue, TypeScript, Python, MongoDB, and prompt engineering—just to name a few. I've contributed to architecture discussions, presented to large audiences, and built features that help streamline processes and make systems more intuitive and efficient. 
      </p>
      <p>
        Beyond work, I’m pursuing a part-time M.S. in Computer Science through Georgia Tech, specializing in Human-Computer Interaction and Interactive Intelligence.
      </p>
      <p>
        In my free time, I love to cook, ballroom dance, explore restaurants, and every now and then rock climb, play volleyball, or get a round of pickleball in with friends.
      </p>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Navbar from '../components/Navbar.vue';

// Dynamically import all images from the assets/img/about_me folder
const images = Object.values(import.meta.glob('../assets/img/about_me/*', { eager: true })).map((module) => module.default);
</script>

<style scoped>
#about-section {
  padding: 2rem 2rem 9rem 2rem ;
  max-width: 900px;
  margin: 0 auto;
}

#about-section h2 {
  font-size: 2.5rem;
  text-align: center;
  color: var(--color-heading);
  margin-bottom: 3rem;
}

.about-container p {
  font-size: 1.2rem;
  line-height: 1.6;
  color: var(--color-text);
  margin-bottom: 3rem;
}

.image-carousel-wrapper {
  margin-top: 10em;
  margin-bottom: 3em;
  width: 100%;
  overflow: hidden;
  position: relative;
}

.image-carousel {
  display: flex;
  width: 100%;
  overflow: hidden;
}

.image-carousel-slide {
  display: flex;
  animation: slide 30s linear infinite;
}

.carousel-image {
  height: 300px;
  object-fit: cover;
  margin: 0 1rem;
}

p {
  text-align: left;
}

@keyframes slide {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}

</style>
