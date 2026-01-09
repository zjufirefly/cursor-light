<template>
  <header
    class="fixed top-0 inset-x-0 z-20 bg-background/95 backdrop-blur border-b border-white/10"
  >
    <nav
      class="max-w-6xl mx-auto flex items-center justify-between px-4 sm:px-6 lg:px-8 h-16"
    >
      <div class="flex items-center gap-3">
        <div
          class="h-9 w-9 rounded-full bg-accent/90 flex items-center justify-center text-background font-bold text-lg"
        >
          F
        </div>
        <div class="leading-tight">
          <p class="font-semibold tracking-wide">Zj-Light Studio</p>
          <!-- <p class="text-xs text-white/60">Contemporary Garment Sample</p> -->
        </div>
      </div>

      <div
        class="hidden md:flex items-center gap-8 ml-5 text-[1.3rem] font-medium"
      >
        <a href="#" class="hover:text-accent transition-colors">首页</a>
        <a href="#collections" class="hover:text-accent transition-colors">产品</a>
        <a href="#about" class="hover:text-accent transition-colors">关于我们</a>
        <a href="#contact" class="hover:text-accent transition-colors">联系方式</a>
      </div>

      <div class="flex-1 flex justify-end">
        <label
          class="relative w-full max-w-xs text-xs text-white/60 focus-within:text-accent"
        >
          <span class="sr-only">搜索服装样品</span>
          <span class="absolute inset-y-0 left-2 flex items-center pointer-events-none">
            <svg
              class="h-4 w-4 text-white/60"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M21 21l-4.35-4.35M10.5 18a7.5 7.5 0 1 1 0-15 7.5 7.5 0 0 1 0 15z"
              />
            </svg>
          </span>
          <input
            v-model="keyword"
            type="search"
            placeholder="搜索：风衣 / 礼服 / 面料工艺..."
            class="w-full bg-white/5 border border-white/10 rounded-full pl-8 pr-3 py-1.5 outline-none placeholder:text-white/40 text-xs focus:border-accent/80 focus:ring-2 focus:ring-accent/40 transition-all"
          />
        </label>
      </div>
    </nav>
  </header>
</template>

<script lang="ts" setup>
import { defineEmits, ref, watch } from 'vue';

const emit = defineEmits<{
  (e: 'search', value: string): void;
}>();

const keyword = ref('');

watch(keyword, (val) => {
  emit('search', val.trim());
});
</script>

