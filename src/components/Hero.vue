<template>
  <section class="relative w-full h-screen flex flex-col items-center justify-center overflow-hidden">
    <!-- Meteor Effects -->
    <div class="absolute inset-0 overflow-hidden">
      <div 
        v-for="(meteor, index) in meteors" 
        :key="index"
        class="absolute h-0.5 w-0.5 rounded-full bg-white opacity-0"
        :style="meteor.style"
      >
        <div class="absolute top-0 left-0 w-20 h-0.5 bg-gradient-to-r from-transparent to-white" style="transform:translateX(-100%)"></div>
      </div>
    </div>
    
    <!-- Floating Circles -->
    <div class="hero-3d absolute -top-20 -left-20 w-[200px] h-[200px] rounded-full bg-gradient-to-br from-[#915eff]/10 to-[#915eff]/5 opacity-40 blur-md hidden md:block" data-depth="0.5"></div>
    <div class="hero-3d absolute bottom-20 -right-10 w-[150px] h-[150px] rounded-full bg-gradient-to-br from-[#00ffff]/10 to-[#00ffff]/5 opacity-30 blur-md hidden md:block" data-depth="0.3"></div>
    
    <!-- Aurora Effect -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] opacity-20 blur-[100px] animate-aurora">
      <div class="absolute inset-0 rounded-full bg-gradient-to-r from-slate-900 via-bg-gray-950 to-slate-900"></div>
    </div>
    
    <!-- Star Field -->
    <div class="absolute inset-0 bg-[url('/star-field.png')] bg-repeat opacity-50"></div>
    
    <!-- Content -->
    <div class="container relative z-10">
      <div class="text-center max-w-4xl mx-auto px-4" ref="heroContent">
        <div class="inline-block mb-6">
          <span class="relative inline-block px-5 py-2 text-sm md:text-base font-medium text-white rounded-full bg-white/10 backdrop-blur-md border border-white/20">
            <span class="absolute top-0 right-0 -mr-2 -mt-2 w-3 h-3 rounded-full bg-bg-gray-900 animate-ping"></span>
            Software Development Agency
          </span>
        </div>
        <h1 class="text-5xl md:text-7xl lg:text-8xl font-bold mb-6">
          <span class="text-slate-50 text-md XTRAHERA">XTRAHERA</span>
        </h1>
        <p class="text-xl md:text-2xl max-w-2xl mx-auto mb-10 text-slate-300" ref="heroSubtitle">
          Mengubah visi digital Anda menjadi realitas dengan solusi<span class="text-slate-50 font-medium"> UI/UX, Web, dan Mobile </span>Development yang inovatif
        </p>
        <div class="flex flex-col sm:flex-row justify-center gap-4" ref="heroButtons">
          <a href="#contact" class="px-8 py-3 bg-gradient-to-r from-slate-900 to-slate-950 rounded-full text-white font-medium hover:shadow-lg hover:shadow-bg-gray-900/30 transition-all duration-300">Konsultasi Gratis</a>
          <a href="#portfolio" class="px-8 py-3 rounded-full border border-white/30 text-white font-medium backdrop-blur-sm hover:bg-white/10 transition-all duration-300">Lihat Portfolio</a>
        </div>
        <div class="hero-3d relative mt-16 mx-auto w-full max-w-md h-20 rounded-3xl overflow-hidden hidden md:block" data-depth="0.2">
          <div class="absolute inset-0 backdrop-blur-lg bg-white/5 border border-white/20"></div>
          <div class="absolute inset-0 flex items-center justify-between px-6">
            <div class="flex items-center gap-4">
              <div class="w-10 h-10 rounded-full bg-gradient-to-r from-slate-900 to-slate-950 flex items-center justify-center">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-circle-check-big w-5 h-5 text-white" aria-hidden="true">
                  <path d="M21.801 10A10 10 0 1 1 17 3.335"></path>
                  <path d="m9 11 3 3L22 4"></path>
                </svg>
              </div>
              <div class="text-left">
                <p class="text-xs text-slate-400">Terpercaya oleh</p>
                <p class="text-white font-medium">50+ Klien</p>
              </div>
            </div>
            <div class="flex items-center -space-x-2">
              <div class="w-8 h-8 rounded-full border-2 border-space-dark bg-gray-800"></div>
              <div class="w-8 h-8 rounded-full border-2 border-space-dark bg-gray-800"></div>
              <div class="w-8 h-8 rounded-full border-2 border-space-dark bg-gray-800"></div>
              <div class="w-8 h-8 rounded-full border-2 border-space-dark bg-gray-800"></div>
              <div class="w-8 h-8 rounded-full border-2 border-space-dark bg-gray-800 flex items-center justify-center text-xs">+</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Scroll Indicator -->
    <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2">
      <div class="w-8 h-12 border-2 border-white/30 rounded-full flex justify-center">
        <div class="w-1 h-3 bg-white rounded-full mt-2 animate-bounce"></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero',
  data() {
    return {
      meteors: []
    }
  },
  mounted() {
    this.generateMeteors();
    this.animateHero();
  },
  methods: {
    generateMeteors() {
      const meteorCount = 15;
      this.meteors = [];
      
      for (let i = 0; i < meteorCount; i++) {
        this.meteors.push({
          style: {
            top: `${Math.random() * 100}%`,
            left: `${Math.random() * 100}%`,
            animation: `meteor ${3 + Math.random() * 5}s linear infinite`,
            animationDelay: `${Math.random() * 10}s`
          }
        });
      }
    },
    animateHero() {
      setTimeout(() => {
        this.$refs.heroContent.style.opacity = 1;
        this.$refs.heroContent.style.transform = 'translateY(0)';
        
        setTimeout(() => {
          this.$refs.heroSubtitle.style.opacity = 1;
          this.$refs.heroSubtitle.style.transform = 'translateY(0)';
          
          setTimeout(() => {
            this.$refs.heroButtons.style.opacity = 1;
            this.$refs.heroButtons.style.transform = 'translateY(0)';
          }, 300);
        }, 300);
      }, 100);
    }
  }
}
</script>

<style scoped>
.animate-aurora {
  animation: aurora 10s infinite linear;
}

@keyframes aurora {
  0% { transform: translate(-50%, -50%) rotate(0deg); }
  100% { transform: translate(-50%, -50%) rotate(360deg); }
}
</style>
