<template>
  <div class="container">
    <TheHeader />
    <span v-if="message">{{ message }}</span>

    <div>
      <div id="px-6 english-quote" class="text-english">{{ english }}</div>
      <AppHr class="m-5" />
      <div id="px-6 japanese-quote" class="text-japanese">{{ japanese }}</div>
      <span class="inline-block m-5"> - </span>
      <div id="author" class="text-author">{{ author }}</div>
    </div>
    <TheFooter />
  </div>
</template>

<script lang="ts">
import { onMounted, ref, reactive, toRefs } from '@vue/composition-api'
import axios from 'axios'
export default {
  setup() {
    const endPoint = process.env.END_POINT || ''
    const message = ref('')
    const result = reactive({
      author: '',
      english: '',
      japanese: '',
    })
    onMounted(async () => {
      try {
        const res: any = await axios.get(endPoint)
        console.log(res)
        result.author = res.data.author
        result.author = res.data.author
        result.english = res.data.english
        result.japanese = res.data.japanese
      } catch (e) {
        message.value = `${e.message}`
      }
    })
    return { ...toRefs(result), message }
  },
}
</script>

<style>
.text-english {
  font-size: 3.2rem;
  font-family: 'freight-display-pro', serif;
  font-weight: 500;
  letter-spacing: -1px;
}
.text-japanese {
  font-size: 3.2rem;
  font-family: 'Noto Serif CJK', serif;
  font-weight: 900;
  font-feature-settings: 'palt';
}
.text-author {
  font-size: 1.4rem;
  font-family: 'freight-display-pro', serif;
  font-weight: 500;
  letter-spacing: -1px;
}
body {
  background-color: #f4f0e7;
  font-family: 'Noto Sans JP', Raleway, HelveticaNeue, 'Helvetica Neue',
    Helvetica, Arial, sans-serif;
  font-weight: 400;
  line-height: 1.6;
  letter-spacing: 0.04em;
  color: #010102;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
}
.container {
  margin: 0 auto;
  min-height: 100vh;
  min-width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
}
</style>
