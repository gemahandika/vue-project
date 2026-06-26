<template>
  <div
    class="min-h-screen bg-gray-50 text-gray-900 dark:bg-gray-900 dark:text-gray-100 font-sans antialiased transition-colors duration-300">
    <header
      class="sticky top-0 z-50 backdrop-blur-md bg-white/70 dark:bg-gray-900/70 border-b border-gray-200 dark:border-gray-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
        <div class="flex items-center gap-3">
          <img src="@/assets/Logogematech.png" alt="Logo Gema Tech"
            class="w-9 h-9 rounded-full object-cover border border-gray-200 shadow-md shadow-gray-200" />
          <span class="text-xl font-bold bg-gradient-to-r from-yellow-500 to-gray-200 bg-clip-text text-transparent">
            Gematech
          </span>
        </div>

        <nav class="hidden md:flex items-center gap-8 text-sm font-medium">
          <a href="#hero"
            class="relative hover:text-indigo-600 dark:hover:text-yellow-400 transition duration-300 after:absolute after:bottom-0 after:left-0 after:h-[2px] after:w-0 after:bg-yellow-400 after:transition-all after:duration-300 hover:after:w-full pb-1">Beranda</a>
          <a href="#skills"
            class="relative hover:text-indigo-600 dark:hover:text-yellow-400 transition duration-300 after:absolute after:bottom-0 after:left-0 after:h-[2px] after:w-0 after:bg-yellow-400 after:transition-all after:duration-300 hover:after:w-full pb-1">Keahlian</a>
          <a href="#portfolio"
            class="relative hover:text-indigo-600 dark:hover:text-yellow-400 transition duration-300 after:absolute after:bottom-0 after:left-0 after:h-[2px] after:w-0 after:bg-yellow-400 after:transition-all after:duration-300 hover:after:w-full pb-1">Portofolio</a>
          <a href="#experience"
            class="relative hover:text-indigo-600 dark:hover:text-yellow-400 transition duration-300 after:absolute after:bottom-0 after:left-0 after:h-[2px] after:w-0 after:bg-yellow-400 after:transition-all after:duration-300 hover:after:w-full pb-1">Pengalaman</a>
        </nav>

        <div class="hidden md:flex items-center gap-4">
          <a :href="`https://wa.me/${nomorWhatsApp}`" target="_blank"
            class="px-4 py-2 text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 rounded-lg transition shadow-md shadow-indigo-500/10">
            Hubungi Kami
          </a>
        </div>

        <button @click="toggleSidebar"
          class="md:hidden p-2 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-800 transition" aria-label="Toggle Menu">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path v-if="!isSidebarOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16" />
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
    </header>

    <div v-if="isSidebarOpen" class="fixed inset-0 z-40 md:hidden bg-black/50 backdrop-blur-sm" @click="toggleSidebar">
    </div>
    <aside :class="[
      isSidebarOpen ? 'translate-x-0' : 'translate-x-full',
      'fixed top-16 right-0 bottom-0 z-40 w-64 bg-white dark:bg-gray-900 border-l border-gray-200 dark:border-gray-800 transition-transform duration-300 ease-in-out md:hidden',
    ]">
      <nav class="flex flex-col gap-4 p-6 text-base font-medium">
        <a href="#hero" @click="toggleSidebar" class="hover:text-indigo-600 transition">Beranda</a>
        <a href="#skills" @click="toggleSidebar" class="hover:text-indigo-600 transition">Keahlian</a>
        <a href="#portfolio" @click="toggleSidebar" class="hover:text-indigo-600 transition">Portofolio</a>
        <a href="#experience" @click="toggleSidebar" class="hover:text-indigo-600 transition">Pengalaman</a>
        <hr class="border-gray-200 dark:border-gray-800 my-2" />
        <a :href="`https://wa.me/${nomorWhatsApp}`" target="_blank"
          class="w-full text-center px-4 py-2.5 text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 rounded-lg transition">
          Hubungi Kami
        </a>
      </nav>
    </aside>

    <main>
      <section id="hero"
        class="relative overflow-hidden pt-12 pb-20 md:pt-20 md:pb-28 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-12 gap-12 items-center">
          <div class="md:col-span-7 flex flex-col justify-center text-center md:text-left">
            <span class="text-white font-semibold uppercase tracking-wider text-xs sm:text-sm mb-2">One-Stop IT
              Solution</span>
            <h1
              class="text-3xl sm:text-3xl lg:text-4xl font-extrabold tracking-tight mb-6 bg-gradient-to-r from-indigo-500 to-white bg-clip-text text-transparent">
              Membangun Bisnis<br />
              <span class="bg-gradient-to-r from-indigo-500 to-gray-400 bg-clip-text text-transparent">Dengan
                Digitalisasi</span>
            </h1>
            <p class="text-lg text-gray-600 dark:text-gray-400 max-w-2xl mx-auto md:mx-0 mb-8 leading-relaxed"
              v-html="deskripsiHero"></p>

            <div class="flex flex-col sm:flex-row items-center justify-center md:justify-start gap-4">
              <a href="#portfolio"
                class="w-full sm:w-auto px-6 py-3.5 text-center text-sm font-semibold text-white bg-indigo-600 hover:bg-indigo-700 rounded-xl transition shadow-lg shadow-indigo-500/20">
                Lihat Riwayat Project
              </a>
              <a :href="`https://wa.me/${nomorWhatsApp}`" target="_blank"
                class="w-full sm:w-auto px-6 py-3.5 text-center text-sm font-semibold text-gray-700 dark:text-gray-200 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-700 rounded-xl transition">
                Kunjungi Toko 🚀
              </a>
            </div>
          </div>

          <div class="md:col-span-5 flex justify-center items-center relative">
            <div
              class="relative transform rotate-2 hover:rotate-0 transition-transform duration-500 ease-out max-w-sm w-full">
              <div class="aspect-square flex items-center justify-center overflow-hidden">
                <img src="@/assets/profile1.png" alt="Gema Tech Hero Illustration"
                  class="w-full h-full object-cover object-center transform hover:scale-105 transition duration-700 ease-out" />
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="skills" class="py-16 bg-white dark:bg-gray-800/50 border-y border-gray-200 dark:border-gray-700">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center max-w-3xl mx-auto mb-12">
            <h2
              class="text-2xl tracking-tight font-bold bg-gradient-to-r from-yellow-500 to-gray-300 bg-clip-text text-transparent">
              Tech Stack & Keahlian
            </h2>
            <p class="text-gray-600 dark:text-gray-400 mt-2">
              Senjata utama yang digunakan untuk mewujudkan ide dan kebutuhan
              digital Anda.
            </p>
          </div>
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-4">
            <div v-for="(skill, index) in keahlian" :key="index" :class="[
              'p-5 bg-white dark:bg-gray-900/60 border rounded-xl text-center text-sm font-semibold hover:scale-105 hover:shadow-lg transition-all duration-300 backdrop-blur-sm flex flex-col justify-center items-center',
              index % 6 === 0 ? 'text-emerald-600 dark:text-emerald-400 border-emerald-200 dark:border-emerald-500/20 hover:border-emerald-500 shadow-emerald-500/5' : '',
              index % 6 === 1 ? 'text-indigo-600 dark:text-indigo-400 border-indigo-200 dark:border-indigo-500/20 hover:border-indigo-500 shadow-indigo-500/5' : '',
              index % 6 === 2 ? 'text-amber-600 dark:text-amber-400 border-amber-200 dark:border-amber-500/20 hover:border-amber-500 shadow-amber-500/5' : '',
              index % 6 === 3 ? 'text-sky-600 dark:text-sky-400 border-sky-200 dark:border-sky-500/20 hover:border-sky-500 shadow-sky-500/5' : '',
              index % 6 === 4 ? 'text-purple-600 dark:text-purple-400 border-purple-200 dark:border-purple-500/20 hover:border-purple-500 shadow-purple-500/5' : '',
              index % 6 === 5 ? 'text-rose-600 dark:text-rose-400 border-rose-200 dark:border-rose-500/20 hover:border-rose-500 shadow-rose-500/5' : '',
            ]">
              <!-- Render Icon SVG Secara Dinamis -->
              <div v-html="skill.icon" class="flex items-center justify-center"></div>

              <!-- Nama Skill -->
              <span class="mt-1 block tracking-wide">{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </section>

      <section id="portfolio" class="py-8 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

        <div class="text-center max-w-3xl mx-auto mb-12">
          <h2
            class="text-2xl tracking-tight font-bold bg-gradient-to-r from-emerald-500 to-gray-300 bg-clip-text text-transparent">
            Production-Ready Apps
          </h2>
          <p class="text-gray-600 dark:text-gray-400 mt-1 text-sm">
            Etalase digital dari sistem yang siap diimplementasikan untuk organisasi atau bisnis Anda.
          </p>
        </div>

        <div class="flex flex-wrap justify-center gap-6 w-full mx-auto">

          <div v-for="(produk, index) in produkList" :key="index"
            class="bg-white dark:bg-gray-800 border border-gray-100 dark:border-gray-700 rounded-xl overflow-hidden shadow-sm hover:shadow-md hover:scale-[1.01] transition-all duration-300 flex flex-col w-full sm:w-[calc(50%-12px)] md:w-[calc(33.33%-16px)] max-w-[350px]">

            <div
              class="relative h-44 w-full bg-gray-100 dark:bg-gray-700 overflow-hidden border-b border-gray-100 dark:border-gray-700">
              <img :src="produk.image" :alt="produk.title"
                class="w-full h-full object-cover object-center transition-transform duration-500 hover:scale-105"
                @error="(e) => (e.target.src = 'https://placehold.co/600x400/1e293b/fff?text=Gema+Tech')" />
              <span
                class="absolute top-3 left-3 text-[10px] font-semibold px-2 py-0.5 bg-indigo-600 text-white rounded-md uppercase tracking-wider">
                {{ produk.category }}
              </span>
            </div>

            <div class="p-4 flex flex-col flex-grow justify-between">
              <div class="mb-4">
                <h3 class="text-base font-bold text-gray-900 dark:text-gray-100 line-clamp-1 mb-1">
                  {{ produk.title }}
                </h3>
                <p class="text-xs text-gray-500 dark:text-gray-400 line-clamp-2 leading-relaxed"
                  v-html="produk.description"></p>
              </div>

              <div
                class="flex items-center justify-between border-t border-gray-50 dark:border-gray-700/50 pt-3 mt-auto">
                <div>
                  <p class="text-[9px] text-gray-400 uppercase tracking-wider font-medium">Mulai Dari</p>
                  <p class="text-sm font-extrabold text-emerald-600 dark:text-emerald-400">{{ produk.price }}</p>
                </div>
                <button @click="selectedProduct = produk"
                  class="px-3 py-1.5 bg-gray-50 dark:bg-gray-700 text-gray-700 dark:text-gray-200 hover:bg-indigo-600 hover:text-white dark:hover:bg-indigo-600 rounded-md transition text-[11px] font-bold shadow-sm">
                  Detail Produk
                </button>
              </div>
            </div>

          </div>

        </div>

        <div class="mt-12 text-center">
          <a href="/projects"
            class="inline-flex items-center gap-2 px-6 py-3 text-sm font-semibold text-gray-700 dark:text-gray-200 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 hover:bg-indigo-600 hover:text-white dark:hover:bg-indigo-600 rounded-xl transition-all duration-300 shadow-sm">
            Lihat Selengkapnya
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
          </a>
        </div>

      </section>

      <section id="experience" class="py-16 bg-white dark:bg-gray-800/50 border-t border-gray-200 dark:border-gray-700">
        <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center max-w-3xl mx-auto mb-12">
            <h2
              class="text-2xl tracking-tight font-bold bg-gradient-to-r from-indigo-500 to-gray-300 bg-clip-text text-transparent">
              Work Experience
            </h2>
            <p class="text-gray-600 dark:text-gray-400 mt-1 text-sm">
              Lini masa perjalanan profesional, peran, dan proyek perangkat lunak yang dibangun untuk mengoptimalkan
              operasional bisnis
            </p>
          </div>
          <div
            class="space-y-8 relative before:absolute before:inset-0 before:left-4 md:before:left-1/2 before:w-0.5 before:bg-gray-200 dark:before:bg-gray-700">
            <div v-for="(item, index) in pengalaman" :key="index"
              class="relative flex flex-col md:flex-row items-start md:justify-between gap-4 md:gap-0 pl-8 md:pl-0">
              <div
                class="absolute left-4 md:left-1/2 w-4 h-4 rounded-full bg-indigo-600 border-4 border-gray-50 dark:border-gray-900 transform -translate-x-1.5 md:-translate-x-2 mt-1.5">
              </div>
              <div :class="[
                index % 2 === 0
                  ? 'md:w-[45%] md:text-right'
                  : 'md:w-[45%] md:ml-auto',
                'w-full bg-white dark:bg-gray-900 border border-gray-100 dark:border-gray-700 p-5 rounded-2xl shadow-sm',
              ]">
                <span class="text-xs font-bold text-indigo-600 dark:text-indigo-400 tracking-wider uppercase">{{
                  item.tahun }}</span>
                <h3 class="text-lg font-bold mt-1 leading-tight">
                  {{ item.posisi }}
                </h3>
                <h4 class="text-sm text-gray-400 font-medium mb-2">
                  {{ item.perusahaan }}
                </h4>
                <p class="text-xs sm:text-sm text-gray-600 dark:text-gray-400 leading-relaxed">
                  {{ item.deskripsi }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer
      class="bg-gray-50 dark:bg-gray-900 border-t border-gray-200 dark:border-gray-800 py-8 text-center text-xs text-gray-500">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row justify-between items-center gap-4">
        <p>© Copyright 2026 Gema Tech. All rights reserved.</p>
        <div class="flex gap-6">
          <a href="#hero" class="hover:underline">Kembali ke Atas</a>
        </div>
      </div>
    </footer>
  </div>
  <div v-if="selectedProduct" class="fixed inset-0 z-[100] overflow-y-auto bg-gray-50 dark:bg-gray-900">
    <ProductDetailView :activeProduct="selectedProduct" :nomorWhatsApp="nomorWhatsApp" @back="selectedProduct = null" />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import ProductDetailView from "./components/ProductDetailView.vue";

const selectedProduct = ref(null);

// 1. Kontak Utama
const nomorWhatsApp = ref("6282168945961");

// 2. State Sidebar Kontrol Mobile
const isSidebarOpen = ref(false);
const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};

// 3. Deskripsi Utama (Menggunakan Tag HTML untuk Teks Tebal)
const deskripsiHero = ref(
  "Kami menyediakan solusi kebutuhan teknologi Anda secara lengkap. Di sini, Anda bisa mendapatkan <b class='text-indigo-600 dark:text-indigo-400 font-bold'>source code aplikasi siap pakai</b>, jasa pembuatan <b class='text-indigo-600 dark:text-indigo-400 font-bold'>website landing page</b> profesional untuk bisnis, hingga berbagai <b class='text-indigo-600 dark:text-indigo-400 font-bold'>aplikasi custom berbasis web</b> untuk mendukung oprasional & management keuangan bisnis anda.",
);

// 4. Data Produk Statis (Tanpa Database)
const produkList = ref([
  // Data 1
  {
    title: "Aplikasi Management Laundry",
    category: "Web Application",
    description:
      "Aplikasi Laundry dirancang untuk membantu operasional laundry dalam pencatatan transaksi, pengelolaan pelanggan, pencetakan nota, dan pembuatan laporan secara cepat dan terstruktur.",
    price: "Rp 1.500.000",
    image: "./laundry.png",
    link: "https://gematech.freedev.app/",
    techStack: "Laravel v11, TailwindCss",
    database: "MySQL",
    features: [
      { title: "Point of Sales (Kasir)", desc: "Pencatatan order pelanggan kiloan/satuan cepat kurang dari 10 detik." },
      { title: "Manajemen Status Status", desc: "Tracking cucian (Antrian, Proses, Selesai, Diambil)." },
      { title: "Invoice Printer", desc: "Cetak nota otomatis untuk printer thermal bluetooth/kasir." },
      { title: "Laporan Keuangan", desc: "Kalkulasi omset harian dan bulanan secara instan." },
      { title: "Diskon & Promo", desc: " Diskon nominal & persentase,  Perhitungan otomatis total pembayaran." },
      { title: "Backup Database", desc: " Backup & Restore Database." }
    ]
  },
  // Data 2
  {
    title: "Aplikasi Management Komunitas Badminton",
    category: "Web Aplication & Landing Page",
    description:
      "Aplikasi Dashboard dan Landing page yang respoonsif , Landing page dapat di atur dari dashboard dan Dashboard memiliki fitur data member dan uang kas (iuran anggota).",
    price: "Rp 1.500.000",
    image: "./app-bulutangkis.jpeg", // <-- Sesuaikan nama file gambar Anda di folder assets
    link: "https://digitaramedan.com",
    techStack: "Laravel v11, Bootstrap CoreUI",
    database: "MySQL / MariaDB",
    features: [
      { title: "Point of Sales (Kasir)", desc: "Pencatatan order pelanggan kiloan/satuan cepat kurang dari 10 detik." },
      { title: "Manajemen Status Status", desc: "Tracking cucian (Antrian, Proses, Selesai, Diambil)." },
      { title: "Invoice Printer", desc: "Cetak nota otomatis untuk printer thermal bluetooth/kasir." },
      { title: "Laporan Keuangan", desc: "Kalkulasi omset harian dan bulanan secara instan." }
    ]
  },

]);

// 5. Data Keahlian
const keahlian = ref([
  {
    name: "Vue.js 3",
    icon: `<svg class="w-7 h-7 mx-auto mb-2" viewBox="0 0 256 221" fill="currentColor"><path d="M204.8 0H256L128 220.8L0 0h51.2L128 132.4L204.8 0z" fill="#41B883"/><path d="M0 0h51.2L128 132.4L204.8 0h51.2L128 220.8L0 0z" fill="#41B883"/><path d="M171.2 0H256L128 220.8L0 0h84.8L128 74L171.2 0z" fill="#35495E"/></svg>`
  },
  {
    name: "Tailwind CSS",
    icon: `<svg class="w-7 h-7 mx-auto mb-2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M24 11.5c-.6 2.5-2.6 4.3-5.2 4.7-2.6.3-5.2-.8-6.8-2.9-1.6 2.1-4.2 3.2-6.8 2.9-2.6-.4-4.6-2.2-5.2-4.7 1-1 2.3-1.6 3.7-1.6 2.3 0 4.3 1.7 4.9 4 .6-2.3 2.6-4 4.9-4 1.4 0 2.7.6 3.7 1.6zm0-5.5c-.6 2.5-2.6 4.3-5.2 4.7-2.6.3-5.2-.8-6.8-2.9-1.6 2.1-4.2 3.2-6.8 2.9-2.6-.4-4.6-2.2-5.2-4.7 1-1 2.3-1.6 3.7-1.6 2.3 0 4.3 1.7 4.9 4 .6-2.3 2.6-4 4.9-4 1.4 0 2.7.6 3.7 1.6z"/></svg>`
  },
  {
    name: "JavaScript (ES6+)",
    icon: `<svg class="w-7 h-7 mx-auto mb-2" fill="currentColor" viewBox="0 0 24 24"><path d="M0 0h24v24H0V0zm21.6 19.12c-.24-1.2-.84-2.12-2.16-2.64-1.08-.36-2.28-.48-2.28-1.32 0-.36.36-.6.96-.6.6 0 .96.24 1.2.72h1.92c-.24-1.44-1.2-2.4-2.88-2.4-1.8 0-3.12 1.08-3.12 2.64 0 1.68 1.44 2.28 3 2.88 1.32.48 1.8.84 1.8 1.56 0 .72-.6 1.08-1.44 1.08-1.08 0-1.68-.48-1.92-1.32h-1.92c.24 2.04 1.56 2.88 3.72 2.88 2.28 0 3.72-1.08 3.72-2.88l-.12-.84zm-9.36-1.56c-.36-.6-.84-.84-1.56-.84-.72 0-1.2.36-1.2.96 0 .72.6.96 1.56 1.32l.72.24c1.56.6 2.4 1.44 2.4 2.88 0 1.92-1.44 3-3.72 3-2.16 0-3.36-1.08-3.72-2.76h1.92c.24.96.84 1.44 1.8 1.44.84 0 1.44-.36 1.44-1.08 0-.72-.36-1.08-1.32-1.44l-.84-.36c-1.44-.48-2.28-1.32-2.28-2.76 0-1.68 1.32-2.64 3.24-2.64 1.68 0 2.88.72 3.36 2.16h-1.92z"/></svg>`
  },
  {
    name: "MySQL",
    icon: `<svg class="w-7 h-7 mx-auto mb-2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4"/></svg>`
  },
  {
    name: "System Integration",
    icon: `<svg class="w-7 h-7 mx-auto mb-2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"/></svg>`
  },
  {
    name: "Laravel",
    icon: `<svg class="w-7 h-7 mx-auto mb-2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/></svg>`
  }
]);

// 6. Data Pengalaman Kerja & Proyek
const pengalaman = ref([

  {
    tahun: "April 2026",
    posisi: "Staff IT Development RSU Hidayah",
    perusahaan: "RSU Hidayah",
    deskripsi:
      "Instalasi SIMRS & Management Data",
  },
  {
    tahun: "Late 2025 - 2026",
    posisi: "Web Developer & Freelance Software Engineer",
    perusahaan: "Freelancer.com & GitHub Integration",
    deskripsi:
      "Membangun, mengembangkan, dan memelihara berbagai aplikasi berbasis web menggunakan stack modern serta mengoptimalkan efisiensi penulisan kode melalui integrasi AI-assisted tools.",
  },
  {
    tahun: "2019-2025",
    posisi: "IT Development / WEB Aplication",
    perusahaan: "Logistic",
    deskripsi:
      "Terlibat aktif dalam proyek pelatihan dan adaptasi platform digital melalui E-LEARNING ONBOARDING CLASS guna mempercepat pemahaman sistem operasional logistik.",
  },
]);

// Bersihkan interval saat komponen tidak lagi dimuat agar hemat memori RAM browser
onUnmounted(() => {
  if (autoSlideInterval) clearInterval(autoSlideInterval);
});
</script>

<style>
html {
  scroll-behavior: smooth;
}
</style>
