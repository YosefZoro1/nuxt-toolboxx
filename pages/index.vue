<template>
  <div>
    <h1>تحويل نص</h1>
    <input type="text" v-model="text" placeholder="أدخل النص هنا">
    <button @click="convertText">تحويل</button>
    <div v-html="result"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: '',
      result: ''
    }
  },
  methods: {
    async convertText() {
      const response = await fetch(`https://aemt.me/gemini?text=${this.text}`);
      const result = await response.json();
      this.result = `<img src="${result.result}" alt="النص المحول">`;
    }
  }
}
</script>

<style scoped>
/* أسلوب التصميم الخاص بك هنا */
</style>
