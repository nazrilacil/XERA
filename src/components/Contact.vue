<template>
  <section id="contact" class="section-padding relative z-10">
    <div class="container">
      <div class="text-center mb-16" ref="sectionTitle">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">
          <span class="text-slate-50">Hubungi Kami</span>
        </h2>
        <p class="text-lg text-slate-400 max-w-2xl mx-auto">Diskusikan ide proyek Anda dan temukan solusi digital bersama kami</p>
      </div>
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
        <!-- Form Kontak -->
        <div class="bg-gray-950/20 backdrop-blur-sm border border-slate-800 rounded-2xl p-6 md:p-8" ref="contactForm">
          <form class="space-y-6" @submit.prevent="submitForm">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label for="name" class="block text-sm font-medium text-slate-300 mb-1">Nama</label>
                <input id="name" type="text" required class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.name" />
              </div>
              <div>
                <label for="email" class="block text-sm font-medium text-slate-300 mb-1">Email</label>
                <input id="email" type="email" required class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.email" />
              </div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label for="phone" class="block text-sm font-medium text-slate-300 mb-1">Telepon</label>
                <input id="phone" type="tel" class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.phone" />
              </div>
              <div>
                <label for="company" class="block text-sm font-medium text-slate-300 mb-1">Perusahaan</label>
                <input id="company" type="text" class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.company" />
              </div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label for="service" class="block text-sm font-medium text-slate-300 mb-1">Layanan yang Dibutuhkan</label>
                <select id="service" class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.service">
                  <option value="" disabled selected>Pilih Layanan</option>
                  <option value="ui/ux">UI/UX Design</option>
                  <option value="web">Web Development</option>
                  <option value="mobile">Mobile Development</option>
                  <option value="other">Lainnya</option>
                </select>
              </div>
              <div>
                <label for="budget" class="block text-sm font-medium text-slate-300 mb-1">Budget (IDR)</label>
                <select id="budget" class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.budget">
                  <option value="" disabled selected>Pilih Budget</option>
                  <option value="&lt; 5jt">Kurang dari 5 Juta</option>
                  <option value="5jt - 10jt">5 - 10 Juta</option>
                  <option value="10jt - 25jt">10 - 25 Juta</option>
                  <option value="25jt - 50jt">25 - 50 Juta</option>
                  <option value="50jt - 100jt">50 - 100 Juta</option>
                  <option value="&gt; 100jt">Lebih dari 100 Juta</option>
                </select>
              </div>
            </div>
            
            <div>
              <label for="message" class="block text-sm font-medium text-slate-300 mb-1">Pesan</label>
              <textarea id="message" rows="4" required class="w-full px-4 py-2 rounded-lg bg-gray-900/50 border border-slate-800 text-white focus:ring-2 focus:ring-bg-gray-900 focus:border-bg-gray-900 outline-none" v-model="formData.message"></textarea>
            </div>
            
            <div>
              <button type="submit" class="w-full py-3 px-6 rounded-lg bg-gradient-to-r from-slate-900 to-slate-950 text-white font-medium hover:shadow-lg hover:shadow-bg-gray-900/20 transition-all">Kirim Pesan</button>
            </div>
          </form>
        </div>
        
        <!-- Informasi Kontak -->
        <div ref="contactInfo">
          <div class="bg-gray-950/20 backdrop-blur-sm border border-slate-800 rounded-2xl p-6 md:p-8 mb-8">
            <h3 class="text-2xl font-bold mb-6 text-white">Informasi Kontak</h3>
            <div class="space-y-4">
              <div class="flex items-start">
                <div class="w-10 h-10 rounded-full bg-bg-gray-950/20 flex items-center justify-center text-bg-gray-950 mr-4">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-phone" aria-hidden="true">
                    <path d="M13.832 16.568a1 1 0 0 0 1.213-.303l.355-.465A2 2 0 0 1 17 15h3a2 2 0 0 1 2 2v3a2 2 0 0 1-2 2A18 18 0 0 1 2 4a2 2 0 0 1 2-2h3a2 2 0 0 1 2 2v3a2 2 0 0 1-.8 1.6l-.468.351a1 1 0 0 0-.292 1.233 14 14 0 0 0 6.392 6.384"></path>
                  </svg>
                </div>
                <div>
                  <h4 class="text-white font-medium">Telepon</h4>
                  <p class="text-slate-400">+62 852 8272 5798</p>
                </div>
              </div>
              
              <div class="flex items-start">
                <div class="w-10 h-10 rounded-full bg-bg-gray-950/20 flex items-center justify-center text-bg-gray-950 mr-4">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-mail" aria-hidden="true">
                    <path d="m22 7-8.991 5.727a2 2 0 0 1-2.009 0L2 7"></path>
                    <rect x="2" y="4" width="20" height="16" rx="2"></rect>
                  </svg>
                </div>
                <div>
                  <h4 class="text-white font-medium">Email</h4>
                  <p class="text-slate-400">info@xtrahera.com</p>
                </div>
              </div>
              
              <div class="flex items-start">
                <div class="w-10 h-10 rounded-full bg-bg-gray-950/20 flex items-center justify-center text-bg-gray-950 mr-4">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-map-pin" aria-hidden="true">
                    <path d="M20 10c0 4.993-5.539 10.193-7.399 11.799a1 1 0 0 1-1.202 0C9.539 20.193 4 14.993 4 10a8 8 0 0 1 16 0"></path>
                    <circle cx="12" cy="10" r="3"></circle>
                  </svg>
                </div>
                <div>
                  <h4 class="text-white font-medium">Alamat</h4>
                  <p class="text-slate-400">Komplek Buana Hilltop View Residence, Kab. Bandung, Jawa Barat</p>
                </div>
              </div>
            </div>
          </div>
          
          <div class="bg-gray-950/20 backdrop-blur-sm border border-slate-800 rounded-2xl p-6 md:p-8">
            <h3 class="text-2xl font-bold mb-6 text-white">Jam Operasional</h3>
            <div class="space-y-2">
              <div class="flex justify-between">
                <span class="text-slate-400">Senin - Jumat</span>
                <span class="text-white">09:00 - 17:00</span>
              </div>
              <div class="flex justify-between">
                <span class="text-slate-400">Sabtu</span>
                <span class="text-white">09:00 - 15:00</span>
              </div>
              <div class="flex justify-between">
                <span class="text-slate-400">Minggu</span>
                <span class="text-white">Tutup</span>
              </div>
            </div>
            <div class="h-px bg-gradient-to-r from-transparent via-slate-700 to-transparent my-6"></div>
            <div class="flex justify-center space-x-4">
              <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-slate-400 hover:bg-bg-gray-900 hover:text-white transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-facebook" aria-hidden="true">
                  <path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path>
                </svg>
              </a>
              <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-slate-400 hover:bg-bg-gray-900 hover:text-white transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-instagram" aria-hidden="true">
                  <rect width="20" height="20" x="2" y="2" rx="5" ry="5"></rect>
                  <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                  <line x1="17.5" x2="17.51" y1="6.5" y2="6.5"></line>
                </svg>
              </a>
              <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-slate-400 hover:bg-bg-gray-900 hover:text-white transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-twitter" aria-hidden="true">
                  <path d="M22 4s-.7 2.1-2 3.4c1.6 10-9.4 17.3-18 11.6 2.2.1 4.4-.6 6-2C3 15.5.5 9.6 3 5c2.2 2.6 5.6 4.1 9 4-.9-4.2 4-6.6 7-3.8 1.1 0 3-1.2 3-1.2z"></path>
                </svg>
              </a>
              <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center text-slate-400 hover:bg-bg-gray-900 hover:text-white transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-linkedin" aria-hidden="true">
                  <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path>
                  <rect width="4" height="12" x="2" y="9"></rect>
                  <circle cx="4" cy="4" r="2"></circle>
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      formData: {
        name: '',
        email: '',
        phone: '',
        company: '',
        service: '',
        budget: '',
        message: ''
      }
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
            }, 100);
          }
        });
      }, { threshold: 0.1 });

      if (this.$refs.sectionTitle) {
        this.$refs.sectionTitle.style.opacity = 0;
        this.$refs.sectionTitle.style.transform = 'translateY(20px)';
        observer.observe(this.$refs.sectionTitle);
      }

      if (this.$refs.contactForm) {
        this.$refs.contactForm.style.opacity = 0;
        this.$refs.contactForm.style.transform = 'translateY(20px)';
        observer.observe(this.$refs.contactForm);
      }

      if (this.$refs.contactInfo) {
        this.$refs.contactInfo.style.opacity = 0;
        this.$refs.contactInfo.style.transform = 'translateY(20px)';
        observer.observe(this.$refs.contactInfo);
      }
    },
    submitForm() {
      // Logika untuk mengirim form
      console.log('Form submitted:', this.formData);
      alert('Terima kasih! Pesan Anda telah terkirim.');
      this.formData = {
        name: '',
        email: '',
        phone: '',
        company: '',
        service: '',
        budget: '',
        message: ''
      };
    }
  }
}
</script>
