<template>
  <div class="flex items-center justify-center min-h-screen">
    <div class="w-[100%] bg-teal-900 text-white rounded-lg shadow-lg">
      <div class="text-center font-bold text-lg p-3 border-b border-teal-10">
        JADWAL PIKET SISWA
      </div>

 
      <div class="px-4 py-2 flex justify-between items-center border-b border-teal-800">
        
        <select class="bg-transparent border-none text-white focus:outline-none">
          <option value="sep">SEP 2024</option>
          <option value="oct">OCT 2024</option>
          <option value="nov">NOV 2024</option>
        </select>
      </div>

      <div class="grid grid-cols-4 text-center border-teal- border-t h-[440px]"> 
        <div class="py-4 border-r border-teal-10 h-full"> 
          <div class="font-bold">Senin</div>
          <div>9</div>
          <div class="mt-2">Fahrul Nabawi</div>
          <button class="flex items-end  px-7 py-1 absolute bottom-2    bg-blue-400 text-teal-900  rounded hover:bg-green-600">
            Edit
          </button>
        </div>

       
        <div class="py-4 border-r border-teal-10 h-full"> 
          <div class="font-bold">Selasa</div>
          <div>10</div>
          <button class="flex items-end  px-7 py-1 absolute bottom-2    bg-blue-400 text-teal-900  rounded hover:bg-green-600">
            Edit
          </button>
        </div>


        <div class="py-4 border-r border-teal-10 h-full"> 
          <div class="font-bold">Rabu</div>
          <div>11</div>
          <button class="flex items-end  px-7 py-1 absolute bottom-2    bg-blue-400 text-teal-900  rounded hover:bg-green-600">
            Edit
          </button>
        </div>

        <div class="py-4 border-r border-teal-10 h-full">
          <div class="font-bold">Kamis</div>
          <div>12</div>
        </div>
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
     
    };
  },
};
</script>

<style scoped>
</style>
