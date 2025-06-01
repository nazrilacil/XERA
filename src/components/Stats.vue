<template>
  <section id="stats" class="section-padding relative z-10">
    <div class="container">
      <div class="bg-gray-950/10 backdrop-blur-sm border border-slate-800 rounded-2xl p-8 md:p-10 overflow-hidden relative">
        <div class="absolute -z-10 top-0 left-0 w-full h-full overflow-hidden">
          <div class="absolute top-0 left-0 w-64 h-64 bg-bg-gray-900/10 rounded-full filter blur-3xl opacity-30 -translate-x-1/2 -translate-y-1/2"></div>
          <div class="absolute bottom-0 right-0 w-80 h-80 bg-bg-gray-950/10 rounded-full filter blur-3xl opacity-30 translate-x-1/2 translate-y-1/2"></div>
        </div>
        
        <div class="text-center mb-10" ref="sectionTitle">
          <h2 class="text-3xl md:text-4xl font-bold mb-2 text-white">Mencapai Keunggulan Bersama</h2>
          <p class="text-slate-400">Angka-angka yang mencerminkan komitmen dan keberhasilan kami dalam industri digital</p>
        </div>
        
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 lg:gap-8">
          <div 
            v-for="(stat, index) in stats" 
            :key="stat.title"
            class="bg-gray-950/50 border border-slate-800 rounded-xl p-6 text-center"
            :ref="`statItem${index}`"
          >
            <div class="w-12 h-12 mx-auto mb-4 flex items-center justify-center text-bg-gray-900">
              <!-- Menggunakan SVG langsung -->
              <svg v-if="stat.icon === 'CheckIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-circle-check-big w-6 h-6" aria-hidden="true">
                <path d="M21.801 10A10 10 0 1 1 17 3.335"></path>
                <path d="m9 11 3 3L22 4"></path>
              </svg>
              
              <svg v-else-if="stat.icon === 'UsersIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-users w-6 h-6" aria-hidden="true">
                <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"></path>
                <path d="M16 3.128a4 4 0 0 1 0 7.744"></path>
                <path d="M22 21v-2a4 4 0 0 0-3-3.87"></path>
                <circle cx="9" cy="7" r="4"></circle>
              </svg>
              
              <svg v-else-if="stat.icon === 'ClockIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-clock w-6 h-6" aria-hidden="true">
                <circle cx="12" cy="12" r="10"></circle>
                <polyline points="12 6 12 12 16 14"></polyline>
              </svg>
            </div>
            <h3 class="text-4xl font-bold mb-1 text-slate-50-static">{{ stat.value }}</h3>
            <p class="text-slate-400">{{ stat.title }}</p>
          </div>
        </div>
        
        <div class="mt-12 flex flex-col sm:flex-row items-center justify-center gap-6">
          <div 
            v-for="(tag, index) in tags" 
            :key="tag.text"
            class="flex items-center"
            :ref="`tagItem${index}`"
          >
            <span class="w-3 h-3 rounded-full mr-2" :class="tag.color"></span>
            <span class="text-slate-300">{{ tag.text }}</span>
          </div>
        </div>
      </div>
      
      <div class="mt-10 grid grid-cols-1 md:grid-cols-3 gap-6">
        <div 
          v-for="(feature, index) in features" 
          :key="feature.title"
          class="bg-gray-950/10 backdrop-blur-sm border border-slate-800 rounded-xl p-6"
          :ref="`featureItem${index}`"
        >
          <div class="flex items-center space-x-4">
            <div class="bg-bg-gray-900/20 p-3 rounded-full">
              <!-- Menggunakan SVG langsung untuk fitur -->
              <svg v-if="feature.icon === 'ZapIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-zap h-6 w-6 text-bg-gray-900" aria-hidden="true">
                <path d="M4 14a1 1 0 0 1-.78-1.63l9.9-10.2a.5.5 0 0 1 .86.46l-1.92 6.02A1 1 0 0 0 13 10h7a1 1 0 0 1 .78 1.63l-9.9 10.2a.5.5 0 0 1-.86-.46l1.92-6.02A1 1 0 0 0 11 14z"></path>
              </svg>
              
              <svg v-else-if="feature.icon === 'ShieldIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-shield h-6 w-6 text-bg-gray-900" aria-hidden="true">
                <path d="M20 13c0 5-3.5 7.5-7.66 8.95a1 1 0 0 1-.67-.01C7.5 20.5 4 18 4 13V6a1 1 0 0 1 1-1c2 0 4.5-1.2 6.24-2.72a1.17 1.17 0 0 1 1.52 0C14.51 3.81 17 5 19 5a1 1 0 0 1 1 1z"></path>
              </svg>
              
              <svg v-else-if="feature.icon === 'LightbulbIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-lightbulb h-6 w-6 text-bg-gray-900" aria-hidden="true">
                <path d="M15 14c.2-1 .7-1.7 1.5-2.5 1-.9 1.5-2.2 1.5-3.5A6 6 0 0 0 6 8c0 1 .2 2.2 1.5 3.5.7.7 1.3 1.5 1.5 2.5"></path>
                <path d="M9 18h6"></path>
                <path d="M10 22h4"></path>
              </svg>
            </div>
            <div>
              <p class="text-xl font-semibold text-white">{{ feature.title }}</p>
              <p class="text-slate-400">{{ feature.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Stats',
  data() {
    return {
      stats: [
        { value: '100+', title: 'Proyek Selesai', icon: 'CheckIcon' },
        { value: '98%', title: 'Kepuasan Klien', icon: 'CheckIcon' },
        { value: '6', title: 'Tenaga Ahli', icon: 'UsersIcon' },
        { value: '2+', title: 'Tahun Pengalaman', icon: 'ClockIcon' }
      ],
      tags: [
        { text: 'Kepuasan Pelanggan Dijamin', color: 'bg-green-500' },
        { text: 'Pengembangan Berkelanjutan', color: 'bg-blue-500' },
        { text: 'Teknologi Terkini', color: 'bg-purple-500' }
      ],
      features: [
        { title: 'Proses Cepat', description: 'Delivery tepat waktu untuk setiap proyek', icon: 'ZapIcon' },
        { title: 'Keamanan Prioritas', description: 'Standar keamanan tertinggi untuk aplikasi', icon: 'ShieldIcon' },
        { title: 'Inovasi Tiada Henti', description: 'Selalu menghadirkan solusi terbaru', icon: 'LightbulbIcon' }
      ]
    }
  },
  mounted() {
    this.initObserver();
  },
  methods: {
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

      // Stats items
      this.stats.forEach((_, index) => {
        const refKey = `statItem${index}`;
        if (this.$refs[refKey] && this.$refs[refKey][0]) {
          const item = this.$refs[refKey][0];
          item.style.opacity = 0;
          item.style.transform = 'translateY(20px)';
          item.dataset.index = index;
          observer.observe(item);
        }
      });

      // Tags
      this.tags.forEach((_, index) => {
        const refKey = `tagItem${index}`;
        if (this.$refs[refKey] && this.$refs[refKey][0]) {
          const item = this.$refs[refKey][0];
          item.style.opacity = 0;
          item.style.transform = 'scale(0.9)';
          item.dataset.index = index;
          observer.observe(item);
        }
      });

      // Features
      this.features.forEach((_, index) => {
        const refKey = `featureItem${index}`;
        if (this.$refs[refKey] && this.$refs[refKey][0]) {
          const item = this.$refs[refKey][0];
          item.style.opacity = 0;
          item.style.transform = 'translateY(20px)';
          item.dataset.index = index;
          observer.observe(item);
        }
      });
    }
  }
}
</script>