<template>
  <section id="team" class="section-padding relative z-10">
    <div class="container">
      <div class="text-center mb-16" ref="sectionTitle">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">
          <span class="text-slate-50">Tim Kami</span>
        </h2>
        <p class="text-lg text-slate-400 max-w-2xl mx-auto">Kenali tim profesional di balik layanan berkualitas SAFCIL DEV</p>
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

      <h3 class="text-2xl font-bold mb-6 text-white" ref="founderTitle">Founder & Co-Founder</h3>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-16">
        <div 
          class="bg-gray-950/20 backdrop-blur-sm border border-slate-800 rounded-2xl overflow-hidden card-hover h-full"
          ref="founderCard1"
          v-for="(founder, index) in founders"
          :key="founder.id"
          :ref="`founderCard${index}`"
        >
          <div class="grid grid-cols-1 md:grid-cols-3 h-full">
            <div class="md:col-span-1 h-72 md:h-auto">
              <div class="h-full w-full overflow-hidden relative">
                <img :src="founder.image" :alt="founder.name" class="absolute inset-0 w-full h-full object-cover object-top" />
              </div>
            </div>
            <div class="p-6 md:col-span-2 flex flex-col h-full">
              <div class="flex-grow">
                <h4 class="text-2xl font-bold mb-1 text-white">{{ founder.name }}</h4>
                <p class="text-bg-gray-900 mb-4">{{  founder.position }}</p>
                <div class="mb-4">
                  <div :class="['text-slate-300', { 'line-clamp-4': !founder.expanded }]">{{ founder.description }}</div>
                <button class="text-bg-gray-900 mt-2 text-sm font-medium hover:underline focus:outline-none"
                @click="founder.expanded = !founder.expanded">
                  {{ founder.expanded ? 'Lihat Lebih sedikit' : 'Lihat Selengkapnya'}}
                </button>
                </div>
                <div class="mb-4">
                  <h5 class="font-medium mb-2">Keahlian:</h5>
                  <div class="flex flex-wrap gap-2">
                    <span class="px-3 py-1 bg-gray-950/20 backdrop-blur-sm border border-slate-700/30 rounded-full text-sm text-white shadow-lg shadow-gray-950/5 hover:shadow-gray-950/10 transition-all"
                    v-for="(skill, skillIndex) in founder.skills"
                    :key="skillIndex"
                    >{{ skill }}</span>
                  </div>
                </div>
              </div>
              <div class="mt-auto pt-4">
                <div class="flex space-x-4 items-center">
                  <a href="https://linkedin.com" class="w-8 h-8 flex items-center justify-center rounded-full bg-slate-800/50 text-slate-400 hover:bg-slate-700 hover:text-white transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-linkedin" aria-hidden="true">
                      <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path>
                      <rect width="4" height="12" x="2" y="9"></rect>
                      <circle cx="4" cy="4" r="2"></circle>
                    </svg>
                  </a>
                  <a href="https://github.com" class="w-8 h-8 flex items-center justify-center rounded-full bg-slate-800/50 text-slate-400 hover:bg-slate-700 hover:text-white transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-github" aria-hidden="true">
                      <path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"></path>
                      <path d="M9 18c-4.51 2-5-2-7-2"></path>
                    </svg>
                  </a>
                  <a href="https://instagram.com" class="w-8 h-8 flex items-center justify-center rounded-full bg-slate-800/50 text-slate-400 hover:bg-slate-700 hover:text-white transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-instagram" aria-hidden="true">
                      <rect width="20" height="20" x="2" y="2" rx="5" ry="5"></rect>
                      <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                      <line x1="17.5" x2="17.51" y1="6.5" y2="6.5"></line>
                    </svg>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <h3 class="text-2xl font-bold mb-6 text-white" ref="teamTitle">Tim Profesional</h3>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        <div 
          v-for="(member, index) in teamMembers" 
          :key="member.id"
          class="bg-gray-950/20 backdrop-blur-sm border border-slate-800 rounded-2xl overflow-hidden card-hover cursor-pointer"
          :ref="`teamMember${index}`"
        >
          <div class="h-56 overflow-hidden">
            <img :src="member.image" :alt="member.name" class="w-full h-full object-cover object-top transition-transform hover:scale-105" />
          </div>
          <div class="p-4 text-center">
            <h4 class="text-xl font-semibold mb-1 text-white">{{ member.name }}</h4>
            <p class="text-bg-gray-900 text-sm mb-3">{{ member.position }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Team',
  data() {
    return {
      activeFilter: 'Semua',
      filters: ['Semua', 'Pendiri', 'UI/UX', 'Web Dev', 'Mobile Dev'],
      teamMembers: [
        { id: 1, name: 'Alifa Salsabila', position: 'UI/UX Designer', image: '/team/alifa.webp' },
        { id: 2, name: 'Hafsah Hamidah', position: 'Web Developer', image: '/team/hafsah.webp' },
        { id: 3, name: 'Shizuka Maulia', position: 'Web Developer', image: '/team/shizuka.webp' },
        { id: 4, name: 'Fathan Putra', position: 'UI/UX Designer', image: '/team/fathan.webp' }
      ],
      founders: [
        {
          id: 1,
          name: 'Nazril Acil',
          position: 'Founder & CEO',
          description: 'Nazril Acil adalah seorang pengembang web (web developer) yang aktif dalam pengembangan perangkat lunak berbasis frontend dan backend. web full-stack yang dikenal karena karya dan kontribusinya dalam edukasi teknologi, beliau mendirikan SAFCIL DEV untuk menyediakan solusi digital berkualitas premium yang menghasilkan dampak nyata bagi klien. Kompetensi utamanya meliputi kepemimpinan teknologi, arsitektur sistem, strategi produk, dan pengembangan bisnis.',
          skills: ['Web Developer','Software Engineer','Tech Enthusiast','Product Strategy','Business Development'],
          image: '/team/ceo.webp',
          expanded: false
        },
        {
          id: 2,
          name: 'Safira Aliyah Azmi',
          position: 'Co-Founder & CMO',
          description: 'Safira Aliyah Azmi adalah spesialis pemasaran digital dengan fokus pada pengembangan merek dan strategi akuisisi pelanggan. Sebagai CMO SAFCIL DEV, beliau mengarahkan inisiatif pemasaran perusahaan dengan pendekatan berbasis data yang didukung pemikiran kreatif untuk mendorong pertumbuhan optimal bagi bisnis klien. Keahliannya mencakup strategi merek, pemasaran digital, growth hacking, pemasaran konten, dan riset pasar.',
          skills: ['Digital Marketing','Brand Strategy','Growth Hacking','Content Marketing','Market Research'],
          image: '/team/cmo.webp',
          expanded: false
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
            }, 150 * parseInt(entry.target.dataset.index));
          }
        });
      }, { threshold: 0.1 });

      // Section title
      if (this.$refs.sectionTitle) {
        this.$refs.sectionTitle.style.opacity = 0;
        observer.observe(this.$refs.sectionTitle);
      }

      // Founder title
      if (this.$refs.founderTitle) {
        this.$refs.founderTitle.style.opacity = 0;
        observer.observe(this.$refs.founderTitle);
      }

      // Founder cards
      if (this.$refs.founderCard1) {
        this.$refs.founderCard1.style.opacity = 0;
        this.$refs.founderCard1.style.transform = 'translateY(20px)';
        this.$refs.founderCard1.dataset.index = 0;
        observer.observe(this.$refs.founderCard1);
      }

      if (this.$refs.founderCard2) {
        this.$refs.founderCard2.style.opacity = 0;
        this.$refs.founderCard2.style.transform = 'translateY(20px)';
        this.$refs.founderCard2.dataset.index = 1;
        observer.observe(this.$refs.founderCard2);
      }

      // Team title
      if (this.$refs.teamTitle) {
        this.$refs.teamTitle.style.opacity = 0;
        observer.observe(this.$refs.teamTitle);
      }

      // Team members
      this.teamMembers.forEach((_, index) => {
        const refKey = `teamMember${index}`;
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
