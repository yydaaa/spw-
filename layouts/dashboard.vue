<template>
  <div class="flex">
    <div class="min-w-52 min-h-screen bg-gray-300 flex flex-col">
      <UVerticalNavigation :links="links">
        <template #default="{ link }">
          <span class="group-hover:text-primary relative" :class="{ 'text-red-700 group-hover:text-red-700': link.label === 'Logout' }">{{ link.label }}</span>
        </template>
      </UVerticalNavigation>
      <div v-if="status == 'error'" class="text-red-500">{{ error.message }}</div>
    </div>
    <div class="container mx-auto px-4 py-10">
      <slot />
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const { execute: logout, status, error } = useAsyncData('logout', async () => {
  const { error } = await supabase.auth.signOut({ scope: 'local' })
  if (error) throw 'Logout gagal'
  else {
    navigateTo('/')
  }
}, {
  immediate: false
})

const links = [
  [
    {
      label: 'Dashboard',
      icon: 'i-heroicons-home',
      to: '/dashboard'
    },

    {
      label: 'Siswa',
      to: '/dashboard/siswa'
    },

    {
      label: 'Kelompok',
      to: '/dashboard/kelompok'
    },

    {
      label:"Guru",
      to: "/dashboard/guru"
    },

    {
      label:"Absen",
      to: "/dashboard/absen"
    },

    {
      label:"Jadwal",
      icon: "heroicons:calendar-20-solid",
      to: "/dashboard/jadwal"
    },

    {
      label:"Piket Siswa",
      to: "/dashboard/jadwalpiketsiswa"
    },

  ],
  [
    {
      label: 'Logout',
      click: () => logout(),
      disabled: status == 'pending'
    }
  ]
]
</script>

<style scoped></style>