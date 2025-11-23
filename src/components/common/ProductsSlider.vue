<template>
  <section class="slider-section container">
    <h2 class="section-title">{{ sectionTitle }}</h2>
    
    <div class="slider-controls">
        <button @click="scroll('right')" class="slider-btn prev-btn">
          <span class="arrow-icon">→</span>
        </button>
        
        <div class="products-wrapper" ref="productsContainer">
            <ProductCard 
                v-for="product in products" 
                :key="product.id" 
                :product="product" 
                @toggle-favorite="handleToggleFavorite"
            />
        </div>
        
        <button @click="scroll('left')" class="slider-btn next-btn">
          <span class="arrow-icon">←</span>
        </button>
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
            const cardElement = container.querySelector('.product-card');

            if (!cardElement) return;

            // 1. حساب مقدار التمرير (عرض البطاقة + الهامش)
            // هذا يضمن أن الحركة تكون بمقدار عرض منتج واحد في كل مرة
            const cardWidth = cardElement.offsetWidth;
            const cardMarginRight = parseInt(window.getComputedStyle(cardElement).marginRight);
            const scrollAmount = cardWidth + cardMarginRight;

            // 2. تطبيق التمرير
            // في وضع RTL، قيمة scrollLeft تتزايد كلما تحركنا نحو بداية القائمة (اليمين)
            
            if (direction === 'right') {
                // التمرير للخلف (نحو اليمين/بداية القائمة)
                container.scrollLeft += scrollAmount;
            } else {
                // التمرير للأمام (نحو اليسار/نهاية القائمة)
                container.scrollLeft -= scrollAmount;
            }
            
            // * ملاحظة: خاصية scroll-behavior: smooth في CSS هي التي تجعل التمرير يتوقف
            // بشكل طبيعي عند حدود المحتوى (السلايدر الطبيعي) *
        },
        handleToggleFavorite(productId) {
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

.section-title {
  text-align: right; 
  margin-bottom: 30px;
  padding: 0 20px;
}

.slider-controls {
    display: flex;
    align-items: center;
    position: relative; 
}

.products-wrapper {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: scroll; 
    scroll-behavior: smooth; // ⬅️ هذا هو سر التوقف الطبيعي
    width: 100%;
    padding: 0 10px; 
    
    // إخفاء شريط التمرير
    &::-webkit-scrollbar { display: none; }
    -ms-overflow-style: none;
    scrollbar-width: none;
}

// الستايل الأنيق للأسهم باللون الذهبي
.slider-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: $accent-color; 
    color: $dark-primary;
    border: none;
    width: 45px;
    height: 45px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 1.5rem;
    line-height: 1;
    z-index: 5;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
    transition: background-color 0.3s, transform 0.3s;
    
    .arrow-icon {
        font-weight: 900;
        display: block; 
    }
    
    &:hover {
        background-color: darken($accent-color, 10%);
        transform: translateY(-50%) scale(1.05);
    }
    
    @media (max-width: 768px) {
        display: none; // إخفاء الأزرار على شاشات الجوال
    }
}

// تحديد مواقع الأزرار في وضع RTL
.prev-btn {
    right: 10px; 
    // السهم يشير لليمين (بداية القائمة)
}

.next-btn {
    left: 10px; 
    // السهم يشير لليسار (نهاية القائمة)
}
</style>