<script setup>
import { getOrderAPI } from '@/apis/pay'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
import { useCountDown } from '@/composables/useCountDown'
const { formatTime, start } = useCountDown()

const route = useRoute()
const payInfo = ref({})
const getPayInfo = async () => {
  const res = await getOrderAPI(route.query.id)
  payInfo.value = res.result
  
  start(res.result.countdown)
}
onMounted(() => getPayInfo())


const baseURL = 'http://pcapi-xiaotuxian-front-devtest.itheima.net/'
const backURL = 'http://127.0.0.1:5173/paycallback'
const redirectUrl = encodeURIComponent(backURL)
const payUrl = `${baseURL}pay/aliPay?orderId=${route.query.id}&redirect=${redirectUrl}`
</script>


<template>
  
</template>

<style scoped lang="scss">

</style>