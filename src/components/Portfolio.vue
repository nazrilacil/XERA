<template>
  <section id="portfolio" class="section-padding relative z-10 overflow-hidden">
    <div class="container">
      <div class="text-center mb-16" ref="sectionTitle">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">
          <span class="text-slate-50">Portfolio Kami</span>
        </h2>
        <p class="text-lg text-slate-400 max-w-2xl mx-auto">Lihat karya terbaik kami dalam mengembangkan solusi digital yang inovatif dan efektif</p>
      </div>

      <div class="flex flex-wrap justify-center gap-4 mb-12">
        <button 
          v-for="(filter, index) in filters" 
          :key="index"
          class="px-6 py-2 rounded-full transition-all"
          :class="[activeFilter === filter ? 'bg-gradient-to-r from-slate-900 to-slate-950 text-white' : 'bg-gray-800/50 hover:bg-gray-800 text-slate-300']"
          @click="activeFilter = filter"
        >
          {{ filter }}
        </button>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in filteredProjects" 
          :key="project.id"
          class="bg-gray-950/20 backdrop-blur-sm rounded-2xl overflow-hidden card-hover"
          :ref="`projectCard${index}`"
        >
          <div class="h-64 overflow-hidden relative">
            <img :src="project.image" :alt="project.title" class="w-full h-full object-cover transition-all duration-300" />
            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-6">
              <h3 class="text-xl font-semibold text-white">{{ project.title }}</h3>
            </div>
          </div>
          <div class="p-6">
            <p class="text-slate-400 mb-4">{{ project.description }}</p>
            <span class="inline-block px-3 py-1 rounded-full text-xs bg-gray-800 text-slate-300 mb-4">{{ project.category }}</span>
            <a :href="project.link" class="text-bg-gray-900 font-medium flex items-center gap-1 hover:text-bg-gray-950 transition-colors">
              Lihat Detail
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-right w-4 h-4" aria-hidden="true">
                <path d="m9 18 6-6-6-6"></path>
              </svg>
            </a>
          </div>
        </div>
      </div>

      <div class="text-center mt-12">
        <button class="px-8 py-3 rounded-full border border-white/30 text-white font-medium backdrop-blur-sm hover:bg-white/10 transition-all duration-300">Lihat Semua Proyek</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Portfolio',
  data() {
    return {
      activeFilter: 'Semua',
      filters: ['Semua', 'UI/UX', 'WEB', 'MOBILE'],
      projects: [
        {
          id: 1,
          title: 'Sociesmedia',
          description: 'Platform pembelajaran inovatif yang dirancang khusus untuk meningkatkan literasi digital dan pemahaman konten edukatif siswa SMP dengan pendekatan interaktif dan gamifikasi.',
          category: 'WEB',
          image: '/projects/sociesmedia.png',
          link: 'https://www.sociesmedia.id/'
        },
        {
          id: 2,
          title: 'Grey Thrift',
          description: 'E-commerce premium untuk produk thrift pilihan dengan UI/UX yang elegan dan sistem pembayaran terintegrasi, menghadirkan pengalaman belanja online yang nyaman dan aman bagi para pecinta fashion.',
          category: 'WEB',
          image: '/projects/greythrift.png',
          link: 'http://rajathriftsepatuscnd.com/'
        },
        {
          id: 3,
          title: 'Yayasan Bersekolah',
          description: 'Platform transparan dan interaktif bagi yayasan penyedia beasiswa, memudahkan calon penerima dalam mengakses informasi, mendaftar program, dan memantau status aplikasi beasiswa mereka secara real-time.',
          category: 'WEB',
          image: '/projects/bersekolah.png',
          link: 'http://bersekolah.vercel.app/'
        }
      ]
    }
  },
  computed: {
    filteredProjects() {
      if (this.activeFilter === 'Semua') return this.projects;
      return this.projects.filter(project => project.category === this.activeFilter);
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

      if (this.$refs.sectionTitle) {
        this.$refs.sectionTitle.style.opacity = 0;
        observer.observe(this.$refs.sectionTitle);
      }

      this.projects.forEach((_, index) => {
        const refKey = `projectCard${index}`;
        if (this.$refs[refKey] && this.$refs[refKey][0]) {
          const card = this.$refs[refKey][0];
          card.style.opacity = 0;
          card.style.transform = 'translateY(20px)';
          card.dataset.index = index;
          observer.observe(card);
        }
      });
    }
  }
}
</script>
