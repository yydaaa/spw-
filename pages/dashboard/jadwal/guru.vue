<template>
  <div class="flex  mb-10">
     <button @click="goBack" class="flex items-center justify-center w-12 h-12 rounded-full border-2 border-gray-400 text-black hover:bg-gray-100">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
    </svg>
  </button>
</div>
  <div class="flex gap-12 mb-10 flex justify-center">
    <UCard class="w-full">
      <template>
        <div class="font-semibold text-center ">JADWAL GURU</div>
      </template>
    </UCard>

  </div>
  <div class="flex justify-between gap-8 w-full text-center">
    <UCard v-for="schedule in schedules" :key="schedule.id" class="w-1/2">

      <template #header>
        <div class="font-semibold">{{ schedule.hari }}</div>
      </template>

      <div v-for="teacher in teachers" :key="teacher.id">{{ teacher.nama }}</div>
    </UCard>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

function goBack() {
  router.back()
}

definePageMeta({
  middleware: 'auth',
  layout: 'dashboard',
})

const supabase = useSupabaseClient()
const user = useSupabaseUser()


const { data: userData } = await useAsyncData('userData', async () => {
  const { data, error } = await supabase.from('users').select('nama, role').eq('id', user.value.id).maybeSingle()
  if (error) throw error
  return data
})


const { data: teachers } = await useAsyncData('teachers', async () => {
  const { data, error } = await supabase.from('guru').select('id, nama').order('id')
  if (error) throw error
  return data
})


const { data: schedules } = await useLazyAsyncData('schedules', async () => {
  const { data, error } = await supabase.from('jadwal').select('id, hari').range(0, 3).order('id')
  if (error) throw error
  return data
})

const selectedId = ref(null)

const state = reactive({
  nama: '',
  kelas: null,
  guru: null,
})
</script>

<style scoped>

</style>
