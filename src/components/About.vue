<template>
  <section id="about" class="section-padding relative z-10">
    <div class="container">
      <div class="text-center mb-16" ref="sectionTitle">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">
          <span class="text-slate-50">Tentang SAFCIL DEV</span>
        </h2>
        <p class="text-lg text-slate-400 max-w-2xl mx-auto">Kami membangun solusi digital yang menarik dan fungsional</p>
      </div>
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <div class="relative" ref="aboutContent">
          <div class="relative z-10">
            <p class="text-slate-300 text-lg mb-6">
              <span class="font-semibold text-white">SAFCIL DEV</span> adalah agensi pengembangan software yang berfokus pada solusi digital komprehensif melalui pendekatan yang inovatif dan berorientasi hasil. Kami percaya bahwa teknologi yang baik harus mempermudah dan memperkaya pengalaman pengguna.
            </p>
            <p class="text-slate-300 text-lg mb-8">
              Dengan tim yang terdiri dari desainer dan developer berpengalaman, kami menyediakan layanan UI/UX Design, Web Development, dan Mobile Development untuk membantu bisnis Anda berkembang di era digital.
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div class="p-6 rounded-2xl bg-gray-950/50 backdrop-blur-sm border border-slate-800">
                <div class="w-12 h-12 rounded-full flex items-center justify-center bg-bg-gray-900/20 text-bg-gray-900 mb-4">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-globe" aria-hidden="true">
                    <circle cx="12" cy="12" r="10"></circle>
                    <path d="M12 2a14.5 14.5 0 0 0 0 20 14.5 14.5 0 0 0 0-20"></path>
                    <path d="M2 12h20"></path>
                  </svg>
                </div>
                <h3 class="font-semibold text-xl mb-2">Visi</h3>
                <p class="text-slate-400">Menjadi pemimpin industri teknologi digital dengan solusi kreatif yang memberdayakan bisnis di seluruh dunia.</p>
              </div>
              
              <div class="p-6 rounded-2xl bg-gray-950/50 backdrop-blur-sm border border-slate-800">
                <div class="w-12 h-12 rounded-full flex items-center justify-center bg-bg-gray-950/20 text-bg-gray-950 mb-4">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-lightbulb" aria-hidden="true">
                    <path d="M15 14c.2-1 .7-1.7 1.5-2.5 1-.9 1.5-2.2 1.5-3.5A6 6 0 0 0 6 8c0 1 .2 2.2 1.5 3.5.7.7 1.3 1.5 1.5 2.5"></path>
                    <path d="M9 18h6"></path>
                    <path d="M10 22h4"></path>
                  </svg>
                </div>
                <h3 class="font-semibold text-xl mb-2">Misi</h3>
                <p class="text-slate-400">Menciptakan solusi digital yang berdampak positif dengan mengutamakan kualitas, inovasi, dan kepuasan klien.</p>
              </div>
            </div>
          </div>
          <div class="absolute -bottom-10 -left-10 w-40 h-40 bg-gradient-to-r from-slate-900/30 to-slate-950/30 rounded-full blur-3xl"></div>
        </div>
        
        <div class="relative" ref="aboutStats">
          <div class="relative z-10 overflow-hidden rounded-2xl border border-slate-800">
            <div class="backdrop-blur-md bg-gray-950/30 p-8">
              <div class="grid grid-cols-2 gap-8">
                <div class="flex flex-col gap-2">
                  <div class="text-4xl font-bold text-bg-gray-900">100+</div>
                  <div class="text-slate-400">Proyek Selesai</div>
                </div>
                <div class="flex flex-col gap-2">
                  <div class="text-4xl font-bold text-bg-gray-950">50+</div>
                  <div class="text-slate-400">Klien Puas</div>
                </div>
              </div>
              
              <div class="h-px bg-gradient-to-r from-transparent via-slate-500/50 to-transparent my-8"></div>
              
              <div class="grid grid-cols-2 gap-8">
                <div class="flex flex-col gap-2">
                  <div class="text-4xl font-bold text-bg-gray-900">2+</div>
                  <div class="text-slate-400">Tahun Pengalaman</div>
                </div>
                <div class="flex flex-col gap-2">
                  <div class="text-4xl font-bold text-bg-gray-950">6</div>
                  <div class="text-slate-400">Tim Profesional</div>
                </div>
              </div>
              
              <div class="mt-8 p-4 rounded-xl bg-gradient-to-r from-slate-900/10 to-slate-950/10 border border-white/5">
                <div class="flex items-center gap-4">
                  <div class="min-w-10 h-10 rounded-full bg-bg-gray-900 flex items-center justify-center text-white">
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-info" aria-hidden="true">
                      <circle cx="12" cy="12" r="10"></circle>
                      <path d="M12 16v-4"></path>
                      <path d="M12 8h.01"></path>
                    </svg>
                  </div>
                  <div>
                    <h4 class="font-medium">Komitmen Kami</h4>
                    <p class="text-sm text-slate-400">Kami berkomitmen untuk memberikan hasil berkualitas tinggi dengan harga yang kompetitif dan tepat waktu</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="absolute -top-10 -right-10 w-40 h-40 bg-gradient-to-r from-slate-950/30 to-slate-900/30 rounded-full blur-3xl"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  mounted() {
    this.initObserver();
  },
  methods: {
    initObserver() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.style.opacity = 1;
            entry.target.style.transform = 'translateX(0)';
            observer.unobserve(entry.target);
          }
        });
      }, { threshold: 0.1 });

      if (this.$refs.sectionTitle) {
        this.$refs.sectionTitle.style.opacity = 0;
        observer.observe(this.$refs.sectionTitle);
      }

      if (this.$refs.aboutContent) {
        this.$refs.aboutContent.style.opacity = 0;
        this.$refs.aboutContent.style.transform = 'translateX(-50px)';
        observer.observe(this.$refs.aboutContent);
      }

      if (this.$refs.aboutStats) {
        this.$refs.aboutStats.style.opacity = 0;
        this.$refs.aboutStats.style.transform = 'translateX(50px)';
        observer.observe(this.$refs.aboutStats);
      }
    }
  }
}
</script>
