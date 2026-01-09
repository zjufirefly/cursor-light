<template>
  <div
    class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5 sm:gap-6 md:gap-7"
  >
    <article
      v-for="item in items"
      :key="item.id"
      class="group relative overflow-hidden rounded-3xl bg-white/5 border border-white/10 shadow-xl shadow-black/40 flex flex-col"
    >
      <div class="relative overflow-hidden">
        <img
          :src="item.image"
          :alt="item.title"
          class="h-60 sm:h-64 w-full object-cover transition-transform duration-700 group-hover:scale-105"
        />
        <div
          class="absolute inset-0 bg-gradient-to-t from-background/90 via-background/10 to-transparent opacity-80"
        ></div>
        <div class="absolute bottom-4 left-4 right-4 flex items-center justify-between">
          <span
            class="inline-flex items-center rounded-full bg-background/80 text-[10px] uppercase tracking-[0.2em] px-3 py-1 text-white/70"
          >
            {{ item.category }}
          </span>
          <span
            class="inline-flex items-center rounded-full bg-accent text-background text-[10px] font-semibold px-2 py-0.5"
          >
            Sample
          </span>
        </div>
      </div>

      <div class="flex-1 flex flex-col px-4 pt-4 pb-4 sm:px-5 sm:pt-4 sm:pb-5">
        <h3 class="text-sm sm:text-base font-semibold mb-1.5 line-clamp-2">
          {{ item.title }}
        </h3>
        <p class="text-xs sm:text-sm text-white/65 line-clamp-3 mb-3">
          {{ item.description }}
        </p>

        <div class="mt-auto flex flex-wrap gap-1.5">
          <span
            v-for="tag in item.tags"
            :key="tag"
            class="inline-flex items-center rounded-full border border-white/10 text-[10px] px-2 py-0.5 text-white/70"
          >
            {{ tag }}
          </span>
        </div>
      </div>
    </article>
  </div>
</template>

<script lang="ts" setup>
export interface CollectionItem {
  id: number;
  title: string;
  category: string;
  description: string;
  image: string;
  tags: string[];
}

defineProps<{
  items: CollectionItem[];
}>();
</script>

