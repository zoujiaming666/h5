<script setup>
import { getOrderAPI } from '@/apis/pay'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
const route = useRoute()
const orderInfo = ref({})

const getOrderInfo = async () => {
  const res = await getOrderAPI(route.query.orderId)
  orderInfo.value = res.result
}

onMounted(() => getOrderInfo())

</script>


<template>
 
</template>

<style scoped lang="scss">

</style>