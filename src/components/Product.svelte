<script>
  import { productData } from '../data/productData.js';
  import headphoneImg from '../assets/headphone-main.png';
</script>

<section id="product" class="scroll-mt-16 py-24 bg-white">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
      
      <!-- Image Section -->
      <div class="relative rounded-2xl overflow-hidden bg-stone-100 aspect-square flex items-center justify-center shadow-inner">
        <img 
          src={headphoneImg} 
          alt="{productData.name}" 
          class="w-full h-full object-cover object-center"
          loading="lazy"
        />
        <div class="absolute inset-0 bg-gradient-to-tr from-black/10 to-transparent"></div>
      </div>

      <!-- Content Section -->
      <div>
        <div class="mb-10">
          <h2 class="text-4xl font-bold text-stone-900 tracking-tight mb-4">{productData.name}</h2>
          <p class="text-xl text-stone-500 font-medium mb-6">{productData.tagline}</p>
          <p class="text-base text-stone-600 leading-relaxed">
            {productData.description}
          </p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 mb-12">
          {#each productData.features as feature}
            <div class="bg-stone-50 p-6 rounded-xl border border-stone-100 hover:shadow-md transition-shadow">
              <h3 class="font-semibold text-stone-900 mb-2">{feature.title}</h3>
              <p class="text-sm text-stone-600 leading-relaxed">{feature.description}</p>
            </div>
          {/each}
        </div>

        <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between border-t border-stone-200 pt-8 mt-8">
          <div class="mb-6 sm:mb-0">
            <span class="block text-sm text-stone-500 mb-1">공식 판매가</span>
            <span class="text-3xl font-bold text-stone-900">{productData.price}</span>
          </div>
          <button class="w-full sm:w-auto px-8 py-4 bg-stone-900 text-white font-semibold rounded-full hover:bg-stone-800 transition-colors shadow-lg hover:shadow-xl transform hover:-translate-y-0.5 active:translate-y-0 duration-200">
            지금 구매하기
          </button>
        </div>
      </div>

    </div>
  </div>
</section>
