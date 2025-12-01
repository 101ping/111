<template>
  <div class="faq-page max-w-4xl mx-auto p-6">
    <h1 class="text-4xl font-bold text-center mb-8">LOONOOL 常见问题</h1>
    
    <div class="space-y-6">
      <div v-for="(item, index) in faqList" :key="index">
        <div 
          class="faq-question cursor-pointer p-4 bg-gray-100 rounded-lg shadow-sm" 
          @click="toggleAnswer(index)"
        >
          <h2 class="text-xl font-semibold">{{ item.question }}</h2>
        </div>
        
        <div 
          v-show="item.isOpen" 
          class="faq-answer mt-4 p-4 bg-gray-50 rounded-lg shadow-inner"
        >
          <p class="text-base">{{ item.answer }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const faqList = ref([
  {
    question: 'LOONOOL 是什么？',
    answer: 'LOONOOL 是一款帮助你判断图片是否适合商用（Safe-to-Use）的工具。你上传一张图片，我们会自动分析视觉、文案和基础行业规则，并生成一份清晰易懂的可用性报告。',
    isOpen: false
  },
  {
    question: 'LOONOOL 和普通相似度工具有什么不同？',
    answer: '大多数相似度工具只告诉你“这张图和别人像不像”。LOONOOL 的关注点不是“像”，而是：“这张图是否适合商用？有没有可能造成视觉混淆或误解？”',
    isOpen: false
  },
  {
    question: 'LOONOOL 适合谁使用？',
    answer: '任何想要“稳一点再用图”的人都能用到 LOONOOL，特别是品牌设计、运营、电商和市场团队。',
    isOpen: false
  },
  {
    question: 'Safe-to-Use 报告里面有什么？',
    answer: 'Safe-to-Use 报告是图片可用性体检，包含视觉稳定性分析、潜在混淆点提示、独特性分析等，旨在评估图片是否适合商用。',
    isOpen: false
  },
  {
    question: 'LOONOOL 会保存我的图片吗？',
    answer: 'LOONOOL 不会长期保存您的图片。原图仅用于分析，最多保留 72 小时，之后自动删除。',
    isOpen: false
  },
  // Add more FAQ items as needed
]);

const toggleAnswer = (index) => {
  faqList.value[index].isOpen = !faqList.value[index].isOpen;
};
</script>

<style scoped>
.faq-question {
  transition: background-color 0.3s ease;
}

.faq-question:hover {
  background-color: #f1f1f1;
}
</style>
