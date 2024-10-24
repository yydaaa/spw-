<template>
      <div class="bg-white  rounded-lg p-9 w-full max-w-4xl ml-11">
        <div class="text-center mb-6">
          <div class="bg-gray-700 min-h-20 text-white py-12  px-4 text-2xl font-semibold  mb-10 shadow-lg rounded-lg ">
             JADWAL PIKET SPW
          </div>
        </div>
        
        <div class="grid grid-cols-4 gap-6">
        
          <div class="bg-teal-700 text-white p-4 rounded-lg">
            <NuxtLink to="jadwal/detail"  class="font-bold text-lg mb-4 ">SENIN</NuxtLink>
            <ul class="space-y-2">
              <li @click="openModal">XI PPLG (4)</li>
              <li @click="openModal">XI TJKT (2)</li>
              <li @click="openModal">XI TBSM (2)</li>
              <li @click="openModal">XI TOI (2)</li>
              <li @click="openModal">XI DKV (2)</li>
            </ul>
            <ul class="mt-4">Deni Manulana</ul>
            <div>Adi Iyasan</div>
          </div>
  
          
          <div class="bg-teal-700 text-white p-4 rounded-lg">
            <NuxtLink to="jadwal/detail"  class="font-bold text-lg mb-4 ">SELASA</NuxtLink>
            <ul class="space-y-2">
              <li @click="openModal">XI PPLG (2)</li>
              <li @click="openModal">XI TJKT (4)</li>
              <li @click="openModal">XI TBSM (2)</li>
              <li @click="openModal">XI TOI (2)</li>
              <li @click="openModal">XI DKV (2)</li>
            </ul>
            <div class="mt-4">Andi</div>
            <div>Ari</div>
          </div>
  
        
          <div class="bg-teal-700 text-white p-4 rounded-lg">
            <div @click="openModal" class="font-bold text-lg mb-4 ">RABU</div>
            <ul class="space-y-2">
              <li @click="openModal">XI PPLG (2)</li>
              <li @click="openModal">XI TJKT (2)</li>
              <li @click="openModal">XI TBSM (4)</li>
              <li @click="openModal">XI TOI (2)</li>
              <li @click="openModal">XI DKV (2)</li>
            </ul>
            <div class="mt-4"></div>
            <div>GURU</div>
          </div>
  
       
          <div class="bg-teal-700 text-white p-4 rounded-lg">
            <h3 class="font-bold text-lg mb-4 ">KAMIS</h3>
            <ul class="space-y-2">
              <li @click="openModal">XI PPLG (2)</li>
              <li @click="openModal">XI TJKT (2)</li>
              <li @click="openModal">XI TBSM (2)</li>
              <li @click="openModal">XI TOI (2)</li>
              <li @click="openModal">XI DKV (4)</li>
            </ul>
            <div class="mt-4">GURU</div>
            <div>GURU</div>
          </div>
        </div>
        
    <div v-if="isModalOpen" class="fixed inset-0 bg-gray-600 bg-opacity-50 flex items-center justify-center z-50">
      <div class="bg-white p-6 rounded-lg shadow-lg relative">
        <h2 class="text-xl font-bold mb-4">Detail Jadwal Piket </h2>
        <table class="table-auto w-full">
          <thead>
            <tr class="bg-gray-100">
              <th class="px-4 py-2">Nama</th>
              <th class="px-4 py-2">Kelas</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="border px-4 py-2">Fahrul</td>
              <td class="border px-4 py-2">XII PPLG 1</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Fahrul</td>
              <td class="border px-4 py-2">XII PPLG 1</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Fahrul</td>
              <td class="border px-4 py-2">XII PPLG 3</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Fahrul</td>
              <td class="border px-4 py-2">XII PPLG 3</td>
            </tr>
          </tbody>
        </table>
       
        <button @click="closeModal" class="absolute top-2 right-2 text-gray-500 hover:text-black">
          &times;
        </button>
      </div>
      </div>
      </div>
  </template>
  
  <script>

  definePageMeta({
    layout: 'dashboard'

  })
  export default {
  data() {
    return {
      isModalOpen: false,  // Untuk mengontrol modal
      selectedDay: '',     // Untuk menyimpan hari yang dipilih
    };
  },
  methods: {
    openModal(day) {
      this.selectedDay = day;  // Set hari yang dipilih
      this.isModalOpen = true; // Tampilkan modal
    },
    closeModal() {
      this.isModalOpen = false; // Tutup modal
    },
  },
};
  </script>
  
  <style scoped>


  </style>
  