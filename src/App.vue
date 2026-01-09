<template>
  <div class="min-h-screen bg-background text-white">
    <TopNav @search="onSearch" />

    <main
      class="pt-20 pb-10 flex flex-col items-center justify-center px-4 sm:px-6 lg:px-8"
    >
      <!-- Hero / Intro -->
      <section
        class="w-full max-w-6xl flex flex-col lg:flex-row items-start lg:items-center gap-10 lg:gap-16 mt-8 mb-10"
      >
        <div class="flex-1 space-y-5">
          <p class="text-xs uppercase tracking-[0.3em] text-accent/80">
            sample collection
          </p>
          <h1 class="text-3xl sm:text-4xl lg:text-5xl font-semibold leading-tight">
            当代服装样品陈列，
            <span class="text-accent">质感与廓形</span>
            的平衡。
          </h1>
          <p class="text-sm sm:text-base text-white/70 max-w-xl">
            精选廓形大衣、礼服与日常基础款，呈现从版型到面料的不同实验向样品，
            适用于 Lookbook、订货会与品牌视觉呈现。
          </p>
          <div class="flex flex-wrap gap-3">
            <span
              class="inline-flex items-center rounded-full border border-accent/60 px-3 py-1 text-xs text-accent/90 bg-accent/5"
            >
              高级成衣
            </span>
            <span
              class="inline-flex items-center rounded-full border border-white/10 px-3 py-1 text-xs text-white/70"
            >
              版型研究
            </span>
            <span
              class="inline-flex items-center rounded-full border border-white/10 px-3 py-1 text-xs text-white/70"
            >
              面料工艺
            </span>
          </div>
        </div>

        <div
          class="flex-1 grid grid-cols-2 gap-3 sm:gap-4 lg:gap-5 max-w-md lg:max-w-none mx-auto"
        >
          <div
            class="col-span-1 row-span-2 rounded-3xl overflow-hidden bg-white/5 border border-white/10 shadow-lg shadow-black/40"
          >
            <img
              src="https://images.pexels.com/photos/6311656/pexels-photo-6311656.jpeg?auto=compress&cs=tinysrgb&w=800"
              alt="结构化廓形大衣"
              class="h-full w-full object-cover hover:scale-105 transition-transform duration-700"
            />
          </div>
          <div
            class="rounded-3xl overflow-hidden bg-white/5 border border-white/10 shadow-lg shadow-black/40"
          >
            <img
              src="https://images.pexels.com/photos/6311587/pexels-photo-6311587.jpeg?auto=compress&cs=tinysrgb&w=800"
              alt="极简礼服细节"
              class="h-full w-full object-cover hover:scale-105 transition-transform duration-700"
            />
          </div>
          <div
            class="rounded-3xl overflow-hidden bg-white/5 border border-white/10 shadow-lg shadow-black/40"
          >
            <img
              src="https://images.pexels.com/photos/6311590/pexels-photo-6311590.jpeg?auto=compress&cs=tinysrgb&w=800"
              alt="面料与纹理实验"
              class="h-full w-full object-cover hover:scale-105 transition-transform duration-700"
            />
          </div>
        </div>
      </section>

      <!-- Collections -->
      <section id="collections" class="w-full max-w-6xl mb-12">
        <div class="flex items-end justify-between mb-6">
          <div>
            <h2 class="text-xl sm:text-2xl font-semibold">样品分类一览</h2>
            <p class="text-sm text-white/60 mt-1">
              根据版型与使用场景划分，快速浏览适配不同设计方向的样衣。
            </p>
          </div>
          <div class="hidden sm:flex gap-2 text-xs">
            <button
              v-for="c in categoriesWithAll"
              :key="c"
              class="px-3 py-1 rounded-full border text-xs transition-colors"
              :class="
                c === activeCategory
                  ? 'bg-accent text-background border-accent'
                  : 'border-white/15 text-white/70 hover:border-accent/60 hover:text-accent'
              "
              @click="activeCategory = c"
            >
              {{ c }}
            </button>
          </div>
        </div>

        <div class="sm:hidden mb-4">
          <label class="block text-xs text-white/60 mb-1">按类别筛选</label>
          <select
            v-model="activeCategory"
            class="w-full bg-white/5 border border-white/15 rounded-md px-3 py-1.5 text-xs outline-none focus:ring-2 focus:ring-accent/50 focus:border-accent/70"
          >
            <option v-for="c in categoriesWithAll" :key="c" :value="c">
              {{ c }}
            </option>
          </select>
        </div>

        <CollectionGrid :items="filteredSamples" />

        <p
          v-if="filteredSamples.length === 0"
          class="mt-8 text-sm text-white/60 text-center"
        >
          暂未找到与
          <span class="text-accent">“{{ searchQuery }}”</span>
          相关的样品，请尝试其他关键字或切换分类。
        </p>
      </section>

      <!-- About & Contact -->
      <section
        id="about"
        class="w-full max-w-6xl grid grid-cols-1 lg:grid-cols-[1.2fr,0.8fr] gap-10 border-t border-white/10 pt-10"
      >
        <div class="space-y-4">
          <h3 class="text-lg font-semibold">关于我们</h3>
          <p class="text-sm text-white/70 leading-relaxed">
            我们是一家专注于当代服装轮廓与工艺研究的样衣工作室，为品牌、设计师与买手店提供小批量展示样品与 Lookbook
            支持。从手工打版到立体裁剪，我们以实验性的方式探索衣服与身体之间更松弛的平衡关系。
          </p>
          <p class="text-sm text-white/70 leading-relaxed">
            当前系列覆盖廓形大衣、结构礼服、职场基础款与运动机能线，适用于发布会陈列、订货会展示与线上视觉内容拍摄。
          </p>
        </div>

        <div id="contact" class="space-y-4">
          <h3 class="text-lg font-semibold">联系方式</h3>
          <div class="space-y-2 text-sm text-white/75">
            <p>商务合作 &amp; 样品预约，请通过以下方式联系：</p>
            <p>
              邮箱：
              <a
                href="mailto:samples@fashionstudio.example"
                class="text-accent hover:underline"
              >
                samples@fashionstudio.example
              </a>
            </p>
            <p>
              电话：
              <span class="text-white/90">+86 010-1234-5678</span>
            </p>
            <p>工作室地址：上海市 静安区 体验路 123 号 · 3F</p>
          </div>
        </div>
      </section>
    </main>

    <SiteFooter />
  </div>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue';
import TopNav from './components/TopNav.vue';
import CollectionGrid from './components/CollectionGrid.vue';
import SiteFooter from './components/SiteFooter.vue';

type SampleCategory = '廓形外套' | '礼服 & 晚装' | '日常基础款' | '运动与机能';

interface SampleItem {
  id: number;
  title: string;
  category: SampleCategory;
  description: string;
  image: string;
  tags: string[];
}

const searchQuery = ref('');
const activeCategory = ref<'全部' | SampleCategory>('全部');

const samples = ref<SampleItem[]>([
  {
    id: 1,
    title: '羊毛混纺廓形大衣 · 深炭灰',
    category: '廓形外套',
    description: '宽肩收腰廓形搭配长款下摆，强调线条与层次感，适用于冬季主推造型。',
    image:
      'https://images.pexels.com/photos/6311579/pexels-photo-6311579.jpeg?auto=compress&cs=tinysrgb&w=900',
    tags: ['长款大衣', '羊毛', '冬季', '结构廓形']
  },
  {
    id: 2,
    title: '不对称剪裁礼服裙 · 黑金',
    category: '礼服 & 晚装',
    description: '侧向不对称下摆与金属光泽面料，适合晚宴与红毯场景。',
    image:
      'https://images.pexels.com/photos/6311585/pexels-photo-6311585.jpeg?auto=compress&cs=tinysrgb&w=900',
    tags: ['晚装', '不对称', '金属光泽']
  },
  {
    id: 3,
    title: '解构西装套装 · 墨黑',
    category: '日常基础款',
    description: '弱化肩线的西装外套搭配高腰长裤，在正式与松弛之间取得平衡。',
    image:
      'https://images.pexels.com/photos/6311662/pexels-photo-6311662.jpeg?auto=compress&cs=tinysrgb&w=900',
    tags: ['西装', '套装', '办公室', '中性']
  },
  {
    id: 4,
    title: '技术面料风衣 · 烟灰色',
    category: '运动与机能',
    description: '轻量防泼水面料与可调节帽檐，强调城市机能与层次搭配。',
    image:
      'https://images.pexels.com/photos/6311589/pexels-photo-6311589.jpeg?auto=compress&cs=tinysrgb&w=900',
    tags: ['风衣', '机能', '防水']
  },
  {
    id: 5,
    title: '针织高领上衣 · 雾白',
    category: '日常基础款',
    description: '贴身但不过度紧绷的高领针织，上身舒适，适合作为内搭打底。',
    image:
      'https://images.pexels.com/photos/6311547/pexels-photo-6311547.jpeg?auto=compress&cs=tinysrgb&w=900',
    tags: ['针织', '高领', '打底']
  },
  {
    id: 6,
    title: '缎面吊带礼服 · 墨蓝',
    category: '礼服 & 晚装',
    description: '顺滑缎面与修身剪裁，适合拍摄与晚宴场合。',
    image:
      'https://images.pexels.com/photos/6311672/pexels-photo-6311672.jpeg?auto=compress&cs=tinysrgb&w=900',
    tags: ['礼服', '缎面', '修身']
  }
]);

const categoriesWithAll = computed<(typeof activeCategory.value)[]>(() => [
  '全部',
  '廓形外套',
  '礼服 & 晚装',
  '日常基础款',
  '运动与机能'
]);

const filteredSamples = computed(() => {
  const keyword = searchQuery.value.toLowerCase();

  return samples.value.filter((item) => {
    const matchCategory =
      activeCategory.value === '全部' || item.category === activeCategory.value;

    const inText =
      !keyword ||
      item.title.toLowerCase().includes(keyword) ||
      item.description.toLowerCase().includes(keyword) ||
      item.tags.some((tag) => tag.toLowerCase().includes(keyword));

    return matchCategory && inText;
  });
});

const onSearch = (value: string) => {
  searchQuery.value = value;
};
</script>

