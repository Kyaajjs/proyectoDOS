<script setup>
import { ref, onMounted } from 'vue'
import { fetchData } from '@/utils/api'
import AdminSidebar from '@/components/admin/AdminSidebar.vue'

const stats = ref(null)

onMounted(async () => {
    stats.value = await fetchData('stats', 'GET')
})
</script>

<template>
    <div class="flex flex-row">
        <AdminSidebar />
        <div class="flex flex-col flex-1 px-16 pt-12 gap-y-8 overflow-auto">
            <div class="text-3xl font-semibold">Dashboard</div>

            <div v-if="stats">
                <!-- Cards -->
                <div class="grid grid-cols-3 gap-6 mb-8">
                    <div class="bg-sky-100 rounded-xl p-6 shadow text-center">
                        <div class="text-4xl font-bold text-sky-600">{{ stats.totalBookings }}</div>
                        <div class="text-gray-600 mt-2">Total Reservas</div>
                    </div>
                    <div class="bg-sky-100 rounded-xl p-6 shadow text-center">
                        <div class="text-4xl font-bold text-sky-600">{{ stats.totalUsers }}</div>
                        <div class="text-gray-600 mt-2">Usuarios</div>
                    </div>
                    <div class="bg-sky-100 rounded-xl p-6 shadow text-center">
                        <div class="text-4xl font-bold text-sky-600">{{ stats.totalSpaces }}</div>
                        <div class="text-gray-600 mt-2">Espacios</div>
                    </div>
                </div>

                <!-- Más info -->
                <div class="grid grid-cols-2 gap-6 mb-8">
                    <div class="bg-white rounded-xl p-6 shadow border border-sky-200">
                        <div class="text-lg font-semibold text-sky-700 mb-2">🏆 Espacio más reservado</div>
                        <div class="text-2xl font-bold">{{ stats.mostBookedSpace.space }}</div>
                        <div class="text-gray-500">{{ stats.mostBookedSpace.count }} reservas</div>
                    </div>
                    <div class="bg-white rounded-xl p-6 shadow border border-sky-200">
                        <div class="text-lg font-semibold text-sky-700 mb-2">👤 Usuario más activo</div>
                        <div class="text-2xl font-bold">{{ stats.mostActiveUser.user }}</div>
                        <div class="text-gray-500">{{ stats.mostActiveUser.count }} reservas</div>
                    </div>
                </div>

                <!-- Reservas por espacio -->
                <div class="bg-white rounded-xl p-6 shadow border border-sky-200 mb-6">
                    <div class="text-lg font-semibold text-sky-700 mb-4">📊 Reservas por espacio</div>
                    <div v-for="item in stats.bookingsBySpace" :key="item.space" class="mb-3">
                        <div class="flex justify-between mb-1">
                            <span class="font-medium">{{ item.space }}</span>
                            <span class="text-gray-500">{{ item.count }}</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div class="bg-sky-500 h-3 rounded-full"
                                :style="{ width: `${(item.count / stats.totalBookings) * 100}%` }">
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Reservas por mes -->
                <div class="bg-white rounded-xl p-6 shadow border border-sky-200">
                    <div class="text-lg font-semibold text-sky-700 mb-4">📅 Reservas por mes</div>
                    <div v-for="item in stats.bookingsByMonth" :key="item.month" class="mb-3">
                        <div class="flex justify-between mb-1">
                            <span class="font-medium">{{ item.month }}</span>
                            <span class="text-gray-500">{{ item.count }}</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div class="bg-emerald-500 h-3 rounded-full"
                                :style="{ width: `${(item.count / stats.totalBookings) * 100}%` }">
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div v-else class="text-gray-400">Cargando estadísticas...</div>
        </div>
    </div>
</template>