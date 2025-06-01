<template>
  <section id="services" class="section-padding relative z-10">
    <div class="container">
      <div class="text-center mb-16" ref="sectionTitle">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">
          <span class="text-slate-50">Layanan Kami</span>
        </h2>
        <p class="text-lg text-slate-400 max-w-2xl mx-auto">Kami menawarkan berbagai layanan digital untuk membantu mengembangkan bisnis Anda</p>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div 
          class="p-6 rounded-2xl bg-gray-950/20 backdrop-blur-md border border-slate-800 hover:border-bg-gray-900/50 transition-all group card-hover" 
          v-for="(service, index) in services" 
          :key="service.title"
          :ref="`serviceCard${index}`"
        >
          <div class="w-14 h-14 rounded-2xl flex items-center justify-center bg-gradient-to-br from-slate-900 to-slate-950 text-white mb-6 group-hover:scale-110 transition-transform">
            <!-- Menggunakan SVG langsung untuk ikon -->
            <svg v-if="service.icon === 'PaletteIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-palette w-6 h-6" aria-hidden="true">
              <path d="M12 22a1 1 0 0 1 0-20 10 9 0 0 1 10 9 5 5 0 0 1-5 5h-2.25a1.75 1.75 0 0 0-1.4 2.8l.3.4a1.75 1.75 0 0 1-1.4 2.8z"></path>
              <circle cx="13.5" cy="6.5" r=".5" fill="currentColor"></circle>
              <circle cx="17.5" cy="10.5" r=".5" fill="currentColor"></circle>
              <circle cx="6.5" cy="12.5" r=".5" fill="currentColor"></circle>
              <circle cx="8.5" cy="7.5" r=".5" fill="currentColor"></circle>
            </svg>
            
            <svg v-else-if="service.icon === 'GlobeIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-globe w-6 h-6" aria-hidden="true">
              <circle cx="12" cy="12" r="10"></circle>
              <path d="M12 2a14.5 14.5 0 0 0 0 20 14.5 14.5 0 0 0 0-20"></path>
              <path d="M2 12h20"></path>
            </svg>
            
            <svg v-else-if="service.icon === 'SmartphoneIcon'" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-smartphone w-6 h-6" aria-hidden="true">
              <rect width="14" height="20" x="5" y="2" rx="2" ry="2"></rect>
              <path d="M12 18h.01"></path>
            </svg>
          </div>
          
          <h3 class="text-2xl font-bold mb-3 text-white">{{ service.title }}</h3>
          <p class="text-slate-400 mb-6">{{ service.description }}</p>
          
          <ul class="space-y-2 mb-6">
            <li v-for="feature in service.features" :key="feature" class="flex items-center gap-2 text-slate-300">
              <span class="text-bg-gray-900">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-check" aria-hidden="true">
                  <path d="M20 6 9 17l-5-5"></path>
                </svg>
              </span>
              {{ feature }}
            </li>
          </ul>
          
          <a href="#contact" class="inline-flex items-center text-bg-gray-900 hover:text-bg-gray-950 transition-colors font-medium">
            Konsultasi
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-arrow-right w-4 h-4 ml-2" aria-hidden="true">
              <path d="M5 12h14"></path>
              <path d="m12 5 7 7-7 7"></path>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Services',
  data() {
    return {
      services: [
        {
          title: 'UI/UX Design',
          description: 'Desain antarmuka pengguna yang menarik dan pengalaman pengguna yang intuitif untuk aplikasi dan website',
          icon: 'PaletteIcon',
          features: [
            'User Research & Analysis',
            'Wireframing & Prototyping',
            'Visual Design & Branding',
            'User Testing & Optimization'
          ]
        },
        {
          title: 'Web Development',
          description: 'Pengembangan website yang responsif, cepat, dan aman dengan teknologi terkini',
          icon: 'GlobeIcon',
          features: [
            'Frontend Development',
            'Backend Development',
            'E-commerce Solutions',
            'CMS & Custom Web Apps'
          ]
        },
        {
          title: 'Mobile Development',
          description: 'Aplikasi mobile yang powerful untuk Android dan iOS dengan performa maksimal',
          icon: 'SmartphoneIcon',
          features: [
            'Native App Development',
            'Cross-platform Development',
            'App Store Optimization',
            'Maintenance & Support'
          ]
        }
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
            }, 100 * parseInt(entry.target.dataset.index));
          }
        });
      }, { threshold: 0.1 });

      if (this.$refs.sectionTitle) {
        this.$refs.sectionTitle.style.opacity = 0;
        observer.observe(this.$refs.sectionTitle);
      }

      this.services.forEach((_, index) => {
        const refKey = `serviceCard${index}`;
        if (this.$refs[refKey] && this.$refs[refKey][0]) {
          const card = this.$refs[refKey][0];
          card.style.opacity = 0;
          card.style.transform = 'translateY(30px)';
          card.dataset.index = index;
          observer.observe(card);
        }
      });
    }
  }
}
</script>