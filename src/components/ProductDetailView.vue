<template>
    <div v-if="activeProduct"
        class="min-h-screen bg-gray-50 text-gray-900 dark:bg-gray-900 dark:text-gray-100 font-sans antialiased pb-20">

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-8">
            <nav class="flex items-center gap-2 text-xs font-medium text-gray-500 dark:text-gray-400">
                <button @click="$emit('back')"
                    class="hover:text-indigo-600 dark:hover:text-emerald-400 transition flex items-center gap-1">
                    <svg class="w-3 h-3" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
                    </svg>
                    Back to Home
                </button>
                <svg class="w-3 h-3 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
                <span class="text-gray-900 dark:text-gray-200 font-semibold">{{ activeProduct.title }}</span>
            </nav>
        </div>

        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-6 grid grid-cols-1 lg:grid-cols-12 gap-10 items-start">

            <section class="lg:col-span-5 space-y-6">
                <div
                    class="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-2xl overflow-hidden shadow-sm">
                    <div class="relative aspect-video w-full bg-gray-100 dark:bg-gray-900">
                        <img :src="activeProduct.image" :alt="activeProduct.title"
                            class="w-full h-full object-cover object-center"
                            @error="(e) => e.target.src = 'https://placehold.co/600x400/1e293b/fff?text=Gema+Tech'" />
                        <span
                            class="absolute top-4 left-4 text-xs font-bold px-2.5 py-1 bg-indigo-600 text-white rounded-md uppercase tracking-wider">
                            {{ activeProduct.category }}
                        </span>
                    </div>
                </div>

                <div
                    class="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-2xl p-6 shadow-sm space-y-4">
                    <div>
                        <p class="text-xs text-gray-400 uppercase tracking-wider font-semibold">Investment Price</p>
                        <p class="text-3xl font-extrabold text-emerald-600 dark:text-emerald-400 mt-1">{{
                            activeProduct.price }}</p>
                        <p class="text-xs text-gray-500 dark:text-gray-400 mt-1">*One-time payment, lifetime source code
                            ownership.</p>
                    </div>

                    <div class="pt-2">
                        <a :href="generateWhatsAppLink(activeProduct.title)" target="_blank"
                            class="w-full inline-flex items-center justify-center gap-2 px-6 py-3.5 text-sm font-bold text-white bg-emerald-600 hover:bg-emerald-700 rounded-xl transition shadow-md shadow-emerald-500/20 text-center cursor-pointer">
                            <svg class="w-5 h-5 fill-currentColor" viewBox="0 0 24 24">
                                <path
                                    d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397 0 11.973 0c3.184.001 6.177 1.242 8.426 3.496 2.248 2.253 3.487 5.244 3.484 8.425-.004 6.625-5.34 11.973-11.916 11.973-2.001-.001-3.97-.504-5.715-1.463L0 24zm6.59-4.846c1.657.983 3.28 1.489 4.954 1.492 5.418 0 9.822-4.387 9.825-9.782.002-2.614-1.013-5.071-2.861-6.921C16.657 2.091 14.204 1.077 11.97 1.077c-5.421 0-9.825 4.388-9.829 9.785-.002 1.83.486 3.62 1.412 5.2l-.999 3.648 3.74-.979z" />
                            </svg>
                            Order via WhatsApp
                        </a>
                    </div>
                    <div class="pt-2">
                        <a :href="activeProduct.link" target="_blank"
                            class="w-full inline-flex items-center justify-center gap-2 px-6 py-3.5 text-sm font-bold text-white bg-indigo-600 hover:bg-indigo-700 rounded-xl transition shadow-md shadow-emerald-500/20 text-center cursor-pointer">

                            link Demo
                        </a>
                    </div>
                </div>
            </section>

            <section class="lg:col-span-7 space-y-8">
                <div>
                    <h1 class="text-3xl font-extrabold tracking-tight text-gray-900 dark:text-gray-100">
                        {{ activeProduct.title }}
                    </h1>
                    <p class="text-sm text-gray-600 dark:text-gray-400 mt-3 leading-relaxed"
                        v-html="activeProduct.description"></p>
                </div>

                <hr class="border-gray-200 dark:border-gray-800" />

                <div class="space-y-4">
                    <h3 class="text-lg font-bold text-gray-900 dark:text-gray-100 flex items-center gap-2">
                        <span class="w-1.5 h-5 bg-indigo-600 rounded-full"></span>
                        Key Features & Capabilities
                    </h3>

                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div v-for="(fitur, idx) in activeProduct.features" :key="idx"
                            class="p-4 bg-white dark:bg-gray-800 border border-gray-100 dark:border-gray-700/60 rounded-xl shadow-sm flex items-start gap-3">
                            <div
                                class="p-1.5 bg-emerald-50 dark:bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 rounded-lg shrink-0">
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5"
                                    viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                                </svg>
                            </div>
                            <div>
                                <h4 class="text-xs font-bold text-gray-900 dark:text-gray-100">{{ fitur.title }}</h4>
                                <p class="text-[11px] text-gray-500 dark:text-gray-400 mt-0.5 leading-relaxed">{{
                                    fitur.desc }}</p>
                            </div>
                        </div>
                    </div>
                </div>

                <hr class="border-gray-200 dark:border-gray-800" />

                <div class="space-y-4">
                    <h3 class="text-lg font-bold text-gray-900 dark:text-gray-100 flex items-center gap-2">
                        <span class="w-1.5 h-5 bg-indigo-600 rounded-full"></span>
                        Technical Architecture
                    </h3>

                    <div
                        class="bg-white dark:bg-gray-800 border border-gray-100 dark:border-gray-700 rounded-xl overflow-hidden">
                        <table class="w-full text-left border-collapse text-xs">
                            <tbody>
                                <tr class="border-b border-gray-100 dark:border-gray-700/50">
                                    <td
                                        class="p-3.5 font-semibold text-gray-500 dark:text-gray-400 w-1/3 bg-gray-50/50 dark:bg-gray-900/20">
                                        Technology Stack</td>
                                    <td class="p-3.5 font-medium text-gray-900 dark:text-gray-100">{{
                                        activeProduct.techStack }}</td>
                                </tr>
                                <tr class="border-b border-gray-100 dark:border-gray-700/50">
                                    <td
                                        class="p-3.5 font-semibold text-gray-500 dark:text-gray-400 bg-gray-50/50 dark:bg-gray-900/20">
                                        Database System</td>
                                    <td class="p-3.5 font-medium text-gray-900 dark:text-gray-100">{{
                                        activeProduct.database }}</td>
                                </tr>
                                <tr>
                                    <td
                                        class="p-3.5 font-semibold text-gray-500 dark:text-gray-400 bg-gray-50/50 dark:bg-gray-900/20">
                                        Deployment Setup</td>
                                    <td
                                        class="p-3.5 font-medium text-emerald-600 dark:text-emerald-400 flex items-center gap-1.5">
                                        <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2"
                                            viewBox="0 0 24 24">
                                            <path stroke-linecap="round" stroke-linejoin="round"
                                                d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
                                        </svg>
                                        Production-Ready (Tinggal Upload ke Hosting)
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>

            </section>
        </main>
    </div>
</template>

<script setup>
// Menangkap data produk yang dikirimkan dari halaman Home utama
defineProps({
    activeProduct: Object,
    nomorWhatsApp: String
});

// Emit event balik ke bapak/induk komponen untuk aksi kembali ke home
defineEmits(['back']);

const generateWhatsAppLink = (namaProduk) => {
    const pesan = encodeURIComponent(`Halo Gematech, saya tertarik dengan source code / aplikasi *${namaProduk}*. Boleh tanya detail sistemnya?`);
    return `https://wa.me/6282168945961?text=${pesan}`;
};
</script>