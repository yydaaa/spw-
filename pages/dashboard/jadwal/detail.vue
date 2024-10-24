<template>
    <div class="flex items-center justify-center">
      <!-- Container untuk tabel dan tombol -->
      <div class="bg-white shadow-lg rounded-lg p-6 relative w-full max-w-lg">
        <!-- Tombol kembali di pojok kiri atas -->
        <NuxtLink to="../jadwal">
        <button class="absolute top-4 left-4 p-2 rounded-full bg-gray-300 hover:bg-gray-400 focus:outline-none">
          <svg class="w-6 h-6 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button></NuxtLink>
  
        <!-- Judul -->
        <h2 class="text-center text-xl font-bold mb-4">DETAIL JADWAL PIKET</h2>
  
        <!-- Tombol Senin di tengah -->
        <div class="flex justify-center mb-6">
          <button class="bg-gray-800 text-white px-4 py-2 rounded-md shadow-lg hover:bg-gray-700 focus:outline-none">
            Senin
          </button>
        </div>
  
        <!-- Tabel Jadwal Piket -->
        <table class="min-w-full border border-teal-700 rounded-lg overflow-hidden">
          <thead class="bg-teal-800 text-white">
            <tr>
              <th class="px-4 py-2 text-left">Nama</th>
              <th class="px-4 py-2 text-left">Kelas</th>
            </tr>
          </thead>
          <tbody class="bg-teal-600 text-white">
            <tr>
              <td class="border border-teal-700 px-4 py-2">Fahrul</td>
              <td class="border border-teal-700 px-4 py-2">XII PPLG 3</td>
            </tr>
            <tr>
              <td class="border border-teal-700 px-4 py-2">Fahrul</td>
              <td class="border border-teal-700 px-4 py-2">XII PPLG 3</td>
            </tr>
          </tbody>
        </table>
  
      </div>
    </div>
  </template>
  
  <script>
    definePageMeta({
    layout: 'dashboard'
  })
  export default {
    name: "DetailJadwalPiket",
  };
  </script>
  
  <style scoped>
  /* Tambahkan styling kustom jika diperlukan */
  </style>
  