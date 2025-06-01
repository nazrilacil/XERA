<template>
  <section id="techstack" class="section-padding relative z-0 overflow-hidden">
    <div class="container">
      <div class="text-center mb-16" ref="sectionTitle">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">
          <span class="text-slate-50">Stack Teknologi</span>
        </h2>
        <p class="text-lg text-slate-400 max-w-2xl mx-auto">Teknologi terkini yang kami gunakan untuk mengembangkan solusi digital</p>
      </div>
      
      <div class="space-y-12">
        <div v-for="(category, catIndex) in techCategories" :key="catIndex" class="mb-10">
          <h3 class="text-2xl font-bold mb-6 text-white capitalize">{{ category.name }}</h3>
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-6">
            <div 
              v-for="(tech, techIndex) in category.techs" 
              :key="tech.name"
              class="bg-gray-950/20 backdrop-blur-sm border border-slate-800 rounded-2xl p-4 flex flex-col items-center justify-center text-center"
              :ref="`techItem${catIndex}${techIndex}`"
            >
              <div class="w-12 h-12 mb-3 flex items-center justify-center">
                <img :src="tech.icon" :alt="tech.name" class="max-w-full max-h-full" />
              </div>
              <span class="text-sm text-slate-300">{{ tech.name }}</span>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Background Dots -->
      <div class="absolute inset-0 -z-10 overflow-hidden">
        <div 
          v-for="(dot, index) in backgroundDots" 
          :key="index"
          class="absolute w-1 h-1 rounded-full bg-bg-gray-900/50"
          :style="dot.style"
        ></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'TechStack',
  data() {
    return {
      techCategories: [
        {
          name: 'Frontend Development',
          techs: [
            { name: 'React', icon: '/tech/react.svg' },
            { name: 'Next.js', icon: '/tech/nextjs.svg' },
            { name: 'Tailwind CSS', icon: '/tech/tailwind.svg' },
            { name: 'TypeScript', icon: '/tech/typescript.svg' }
          ]
        },
        {
          name: 'Backend Development',
          techs: [
            { name: 'Node.js', icon: '/tech/nodejs.svg' },
            { name: 'Laravel', icon: '/tech/laravel.svg' }
          ]
        },
        {
          name: 'Mobile Development',
          techs: [
            { name: 'Flutter', icon: '/tech/flutter.svg' },
            { name: 'Kotlin', icon: '/tech/kotlin.svg' }
          ]
        },
        {
          name: 'UI/UX Design',
          techs: [
            { name: 'Figma', icon: '/tech/figma.svg' }
          ]
        },
        {
          name: 'Database & Storage',
          techs: [
            { name: 'MySQL', icon: '/tech/mysql.svg' },
            { name: 'Firebase', icon: '/tech/firebase.svg' }
          ]
        },
        {
          name: 'DevOps & Infrastructure',
          techs: [
            { name: 'Docker', icon: '/tech/docker.svg' }
          ]
        }
      ],
      backgroundDots: []
    }
  },
  mounted() {
    this.generateBackgroundDots();
    this.initObserver();
  },
  methods: {
    generateBackgroundDots() {
      const dotCount = 10;
      this.backgroundDots = [];
      
      for (let i = 0; i < dotCount; i++) {
        this.backgroundDots.push({
          style: {
            top: `${Math.random() * 100}%`,
            left: `${Math.random() * 100}%`
          }
        });
      }
    },
    initObserver() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            setTimeout(() => {
              entry.target.style.opacity = 1;
              entry.target.style.transform = 'translateY(0)';
              observer.unobserve(entry.target);
            }, 150 * parseInt(entry.target.dataset.index));
          }
        });
      }, { threshold: 0.1 });

      // Section title
      if (this.$refs.sectionTitle) {
        this.$refs.sectionTitle.style.opacity = 0;
        observer.observe(this.$refs.sectionTitle);
      }

      // Tech items
      this.techCategories.forEach((category, catIndex) => {
        category.techs.forEach((_, techIndex) => {
          const refKey = `techItem${catIndex}${techIndex}`;
          if (this.$refs[refKey] && this.$refs[refKey][0]) {
            const item = this.$refs[refKey][0];
            item.style.opacity = 0;
            item.style.transform = 'translateY(20px)';
            item.dataset.index = catIndex * 10 + techIndex;
            observer.observe(item);
          }
        });
      });
    }
  }
}
</script>
