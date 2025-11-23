<template>
  <section class="slider-section container">
    <h2 class="section-title">{{ sectionTitle }}</h2>
    
    <div class="slider-controls">
        <button @click="scroll('left')" class="slider-btn"> &lt; </button>
        
        <div class="products-wrapper" ref="productsContainer">
            <ProductCard 
                v-for="product in products" 
                :key="product.id" 
                :product="product" 
                @toggle-favorite="handleToggleFavorite"
            />
        </div>
        
        <button @click="scroll('right')" class="slider-btn"> &gt; </button>
    </div>
  </section>
</template>

<script>
import ProductCard from '../sections/ProductCard.vue';

export default {
    name: 'ProductsSlider',
    components: { ProductCard },
    props: {
        sectionTitle: String,
        products: Array
    },
    methods: {
        scroll(direction) {
            const container = this.$refs.productsContainer;
            const scrollAmount = container.clientWidth / 2; // التمرير بنصف عرض الحاوية
            
            if (direction === 'left') {
                container.scrollLeft -= scrollAmount;
            } else {
                container.scrollLeft += scrollAmount;
            }
        },
        handleToggleFavorite(productId) {
            // هنا يمكنك إرسال حدث إلى المكون الأب (App.vue) لتحديث حالة المنتج
            this.$emit('toggle-favorite-product', productId);
        }
    }
};
</script>

<style lang="scss" scoped>
@import '../../assets/styles/_variables.scss';

.slider-section {
    padding: 40px 0;
}

.slider-controls {
    display: flex;
    align-items: center;
    // للحفاظ على الأزرار خارج مساحة المنتجات
    margin: 0 -20px; 
}

.products-wrapper {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: scroll; // الخاصية التي تتيح التمرير الأفقي
    scroll-behavior: smooth;
    width: 100%;
    
    // إخفاء شريط التمرير
    &::-webkit-scrollbar { display: none; }
    -ms-overflow-style: none;
    scrollbar-width: none;
}

.slider-btn {
    background-color: $button-bg;
    color: $light-text;
    border: none;
    padding: 10px 15px;
    margin: 0 10px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 1.5rem;
    line-height: 1;
    flex-shrink: 0; 
    transition: background-color 0.3s;
    
    &:hover {
        background-color: $accent-color;
        color: $dark-primary;
    }
    
    // إخفاء الأزرار على الجوال إذا كانت المساحة ضيقة
    @media (max-width: 600px) {
        display: none; 
    }
}
</style>