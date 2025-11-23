<template>
  <div id="app-container">
    <AppHeader /> 
    
    <main>
      <HeroSection /> 
      <ProductsSlider sectionTitle="أحدث المنتجات" :products="latestProducts" />
      <WhyChooseUs />
      <ProductsSlider sectionTitle="الأكثر تداولاً" :products="trendingProducts" />
      <StorySection />
      <FAQSection />
      </main>
    
    <AppFooter />
  </div>
</template>

<script>
// المسارات تبدأ من 'src/' لأن App.vue موجود في src/

// مكونات الـ Layout
import AppHeader from './components/layout/AppHeader.vue'; 
import AppFooter from './components/layout/AppFooter.vue';

// مكونات عامة
import ProductsSlider from './components/common/ProductsSlider.vue'; 

// مكونات الأقسام (أضف باقي الاستيرادات هنا لاحقاً)
import HeroSection from './components/sections/HeroSection.vue';
import StorySection from './components/sections/StorySection.vue';
import WhyChooseUs from './components/sections/WhyChooseUs.vue';
import FAQSection from './components/sections/FAQSection.vue';

import productImg1 from './assets/imgs/0dd17c99d7d31d1b7dca7cbe7259c536.jpg'; // ساعة القمر
import productImg2 from './assets/imgs/12b7dfb1de3206f402c2b55a1204aa62 (1).jpg'; // مصباح الهلال
import productImg3 from './assets/imgs/4eb4444f37fc2fe43000b6d1151ea01e.jpg'; // رفوف الخشب والأضواء
import productImg4 from './assets/imgs/193eec689430c83928d7a9e99c4ceb09.jpg';  
import productImg5 from './assets/imgs/1.jpg'; 
import productImg6 from './assets/imgs/7b27cd6499dc0c5da56bc20f7cc33429.jpg';  
import productImg7 from './assets/imgs/ac26ade7d84cfda976085066cd5ad590.jpg';  
import productImg8 from './assets/imgs/51761f1e6ab10512291628816c007f14.jpg';  


export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter,
    ProductsSlider,
    HeroSection,
    StorySection,
    WhyChooseUs,
    FAQSection
  },
  data() {
      // يمكنك استخدام Pinia أو Vuex لإدارة المنتجات بدلاً من البيانات المحلية
      return {
          latestProducts: [
              { id: 1, name: 'مصابيح مرنة', price: '٣٠٠', isFavorite: false, imageUrl: productImg1 },
              { id: 2, name: 'مصباح ليلي طويل', price: '٨٠٠', isFavorite: true, imageUrl: productImg2 },
              { id: 3, name: 'طاولة خشب', price: '١١٠٠', isFavorite: false, imageUrl: productImg3 },
              { id: 4, name: 'إناء فني', price: '٤٥٠', isFavorite: false, imageUrl: productImg4 },
              { id: 5, name: 'لوحة حائط', price: '٧٥٠', isFavorite: false, imageUrl:  productImg5 },
          ], 
          trendingProducts: [
              { id: 6, name: 'ملصقات حائط', price: '١٥٠', isFavorite: false, imageUrl: productImg6 },
              { id: 7, name: 'أكواب قهوة', price: '٢٠٠', isFavorite: false, imageUrl: productImg7 },
              { id: 7, name: ' قهوة', price: '1٠٠', isFavorite: false, imageUrl: productImg8},
          ]
      }
  }
};
</script>