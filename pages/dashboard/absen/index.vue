<template>
    <div class="flex justify-center items-center h-screen bg-gray-50">
      <div class="bg-white rounded-lg shadow-lg p-6 w-full max-w-md">
        <h2 class="text-center font-bold text-xl mb-4 text-gray-700">ABSENSI</h2>
  
        <!-- Form -->
        <form @submit.prevent="submitAbsensi" class="space-y-4">
          <!-- Nama -->
          <div>
            <label class="block text-sm font-semibold text-gray-600 mb-2">Nama</label>
            <select v-model="selectedNama" class="block w-full bg-white border border-gray-300 rounded-md p-2 text-sm text-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-400">
              <option value="" disabled>Pilih Nama</option>
              <option v-for="siswa in siswaList" :key="siswa.id" :value="siswa.nama">
                {{ siswa.nama }}
              </option>
            </select>
          </div>
  
          <!-- Kategori -->
          <div>
            <label class="block text-sm font-semibold text-gray-600 mb-2">Kategori</label>
            <select v-model="kategori" class="block w-full bg-white border border-gray-300 rounded-md p-2 text-sm text-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-400">
              <option value="Siswa">Siswa</option>
              <option value="Guru">Guru</option>
            </select>
          </div>
  
          <!-- Tingkat, Jurusan, Kelas -->
          <div class="grid grid-cols-3 gap-4">
            <div>
              <label class="block text-sm font-semibold text-gray-600 mb-2">Tingkat</label>
              <select v-model="tingkat" class="block w-full bg-white border border-gray-300 rounded-md p-2 text-sm text-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-400">
                <option>Pilih Tingkat</option>
                <!-- Tambahkan opsi tingkat di sini -->
              </select>
            </div>
            <div>
              <label class="block text-sm font-semibold text-gray-600 mb-2">Jurusan</label>
              <select v-model="jurusan" class="block w-full bg-white border border-gray-300 rounded-md p-2 text-sm text-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-400">
                <option>Pilih Jurusan</option>
                <!-- Tambahkan opsi jurusan di sini -->
              </select>
            </div>
            <div>
              <label class="block text-sm font-semibold text-gray-600 mb-2">Kelas</label>
              <select v-model="kelas" class="block w-full bg-white border border-gray-300 rounded-md p-2 text-sm text-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-400">
                <option>Pilih Kelas</option>
                <!-- Tambahkan opsi kelas di sini -->
              </select>
            </div>
          </div>
  
          <!-- Submit Button -->
          <div class="flex justify-center mt-4">
            <button type="submit" class="bg-green-500 text-white rounded-md py-2 px-4 shadow-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500">
              Kirim
            </button>
          </div>
        </form>
      </div>
    </div>
  </template>
  
  <script setup>
  // Menggunakan Supabase Client dan User
  const supabase = useSupabaseClient()
  const user = useSupabaseUser()
  
  // Variabel data
  const siswaList = ref([])
  const selectedNama = ref('')
  const kategori = ref('Siswa')
  const tingkat = ref('')
  const jurusan = ref('')
  const kelas = ref('')
  
  // Fetch data siswa dari Supabase ketika komponen di-mount
  onMounted(async () => {
    const { data, error } = await supabase
      .from('siswa')
      .select('id, nama')
  
    if (error) {
      console.error('Error fetching siswa:', error)
    } else {
      siswaList.value = data
    }
  })
  
  // Fungsi submit absensi
  const submitAbsensi = async () => {
    const { error } = await supabase
      .from('kehadiran')
      .insert([
        {
          nama: selectedNama.value,
          kategori: kategori.value,
          tingkat: tingkat.value,
          jurusan: jurusan.value,
          kelas: kelas.value,
          user_id: user.value?.id || null // Optional: menautkan ke user Supabase yang sedang login
        }
      ])
  
    if (error) {
      console.error('Error inserting kehadiran:', error)
    } else {
      alert('Absensi berhasil dikirim!')
  
      // Reset form setelah submit
      selectedNama.value = ''
      kategori.value = 'Siswa'
      tingkat.value = ''
      jurusan.value = ''
      kelas.value = ''
    }
  }
  </script>
  
  <style scoped>
  /* Sesuaikan styling dengan Tailwind */
  </style>
  