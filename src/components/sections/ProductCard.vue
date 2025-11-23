<template>
  <div class="product-card">
    <div class="product-image-container">
      <img :src="product.imageUrl" :alt="product.name" class="product-image">
      
      <button 
        @click="toggleWishlist" 
        :class="['wishlist-btn', { 'is-favorite': product.isFavorite }]"
      >
        {{ product.isFavorite ? '♥' : '♡' }} 
      </button>
    </div>
    
    <div class="product-info">
      <p class="product-name">{{ product.name }}</p>
      <p class="product-price">{{ product.price }} ر.س</p>
      
      <button @click="addToCart" class="add-to-cart-btn">
        إضافة للسلة
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
      product: {
          type: Object,
          required: true
      }
  },
  methods: {
    addToCart() {
      // هنا تضع منطق إضافة المنتج للسلة (عن طريق Pinia أو Vuex)
      console.log(`تمت إضافة ${this.product.name} إلى السلة.`);
    },
    toggleWishlist() {
      // هنا تضع منطق تبديل حالة المفضلة (عن طريق Pinia أو تحديث محلي)
      this.$emit('toggle-favorite', this.product.id);
      console.log(`تبديل مفضلة لـ ${this.product.name}.`);
    }
  }
};
</script>

<style lang="scss" scoped>
@import '../../assets/styles/_variables.scss'; 

.product-card {
  display: flex;
  flex-direction: column;
  background-color: #3e161c; // خلفية أغمق للبطاقة
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
  margin: 10px;
  min-width: 250px; // لضمان عرض مناسب في السلايدر
}

.product-image-container {
  position: relative;
  overflow: hidden;
}

.product-image {
  width: 100%;
  height: 250px; 
  object-fit: cover;
  display: block;
}

.wishlist-btn {
  // تنسيق زر المفضلة
  position: absolute;
  top: 10px;
  right: 10px;
  background: rgba(255, 255, 255, 0.9);
  // ... (باقي الستايلات من المثال السابق)
  border-radius: 50%;
  width: 35px;
  height: 35px;
  font-size: 20px;
  cursor: pointer;
  color: $dark-primary;
  border: none;
  
  &.is-favorite {
    color: #e74c3c; // أحمر عند التفضيل
  }
}

.product-info {
  padding: 15px;
  text-align: center;
}

.product-name {
  font-size: 1.1rem;
  margin-bottom: 5px;
}

.product-price {
  font-size: 1.6rem;
  font-weight: bold;
  color: $accent-color; 
  margin-bottom: 15px;
}

.add-to-cart-btn {
  // تنسيق زر الإضافة للسلة
  width: 100%;
  padding: 12px;
  background-color: $button-bg;
  color: $light-text;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
  font-weight: bold;
  
  &:hover {
    background-color: darken($button-bg, 10%);
  }
}
</style>