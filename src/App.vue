<template>
  <div class="bg-black text-white overflow-x-hidden">
    <!-- Background Elements -->
    <div class="gradient-mesh fixed inset-0 -z-20 pointer-events-none">
      <div class="gradient-circle gradient-circle-1"></div>
      <div class="gradient-circle gradient-circle-2"></div>
      <div class="gradient-circle gradient-circle-3"></div>
      <div class="gradient-circle gradient-circle-4"></div>
      <div class="gradient-circle gradient-circle-5"></div>
      <div class="gradient-circle gradient-circle-6"></div>
    </div>
    
    <div class="stars-container fixed inset-0 -z-10 pointer-events-none">
      <div class="stars"></div>
      <div class="stars2"></div>
      <div class="stars3"></div>
    </div>

    <!-- Components -->
    <Navbar />
    <main class="overflow-hidden">
      <Peromo />
      <Hero />
      <About />
      <Services />
      <Portfolio />
      <Team />
      <TechStack />
      <Stats />
      <Contact />
    </main>
    <Footer />
  </div>
</template>

<script>
import Peromo from './components/Peromo.vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Services from './components/Services.vue'
import Portfolio from './components/Portfolio.vue'
import Team from './components/Team.vue'
import TechStack from './components/TechStack.vue'
import Stats from './components/Stats.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Peromo,
    Navbar,
    Hero,
    About,
    Services,
    Portfolio,
    Team,
    TechStack,
    Stats,
    Contact,
    Footer
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@700&display=swap');

:root {
  --space-dark: #0f172a;
}

html, body {
  font-family: 'Inter', sans-serif;
  scroll-behavior: smooth;
}

.gradient-mesh {
  position: fixed;
  inset: 0;
  z-index: -20;
  pointer-events: none;
}

.gradient-circle {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
}

.gradient-circle-1 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(145, 94, 255, 0.2) 0%, transparent 70%);
  top: 20%;
  left: 10%;
}

.gradient-circle-2 {
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(0, 255, 255, 0.15) 0%, transparent 70%);
  bottom: 10%;
  right: 10%;
}

.gradient-circle-3 {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(255, 105, 180, 0.15) 0%, transparent 70%);
  top: 40%;
  right: 20%;
}

.gradient-circle-4 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(50, 205, 50, 0.1) 0%, transparent 70%);
  bottom: 20%;
  left: 20%;
}

.gradient-circle-5 {
  width: 350px;
  height: 350px;
  background: radial-gradient(circle, rgba(255, 215, 0, 0.1) 0%, transparent 70%);
  top: 60%;
  left: 30%;
}

.gradient-circle-6 {
  width: 450px;
  height: 450px;
  background: radial-gradient(circle, rgba(138, 43, 226, 0.1) 0%, transparent 70%);
  top: 30%;
  right: 30%;
}

.stars-container {
  position: fixed;
  inset: 0;
  z-index: -10;
  pointer-events: none;
  overflow: hidden;
}

.stars,
.stars2,
.stars3 {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background-image: 
    radial-gradient(1px 1px at 20% 30%, #fff, rgba(0,0,0,0)),
    radial-gradient(1px 1px at 40% 70%, #fff, rgba(0,0,0,0)),
    radial-gradient(1px 1px at 60% 10%, #fff, rgba(0,0,0,0)),
    radial-gradient(1px 1px at 80% 90%, #fff, rgba(0,0,0,0)),
    radial-gradient(1px 1px at 30% 50%, #fff, rgba(0,0,0,0)),
    radial-gradient(1px 1px at 70% 20%, #fff, rgba(0,0,0,0));
  background-repeat: repeat;
  background-size: 200px 200px;
  opacity: 0.2;
}

.stars2 {
  background-size: 300px 300px;
  opacity: 0.15;
  animation: animStar 150s linear infinite;
}

.stars3 {
  background-size: 400px 400px;
  opacity: 0.1;
  animation: animStar 200s linear infinite;
}

@keyframes animStar {
  from { transform: translateY(0); }
  to { transform: translateY(-1000px); }
}

@keyframes meteor {
  0% { opacity: 1; transform: translateX(0) rotate(215deg); }
  70% { opacity: 1; }
  100% { transform: translateX(-300px) rotate(215deg); opacity: 0; }
}

.section-padding {
  padding: 120px 0;
  position: relative;
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Animations */
[style*="opacity:0"] {
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.card-hover {
  transition: all 0.3s ease;
}

.card-hover:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.1);
}

/* Responsive */
@media (max-width: 768px) {
  .section-padding {
    padding: 80px 0;
  }
  
  .container {
    padding: 0 15px;
  }
}
</style>