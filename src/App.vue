<template>
  <div>
    <!-- Navbar -->
    <header>
      <div class="container navbar">
        <div class="logo">أركان</div>
        <div class="nav-links">
          <a href="#">الرئيسية</a>
          <a href="#">المنتجات</a>
          <a href="#">عن أركان</a>
          <a href="#">تواصل</a>
        </div>
      </div>
    </header>

    <!-- Hero -->
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h1>مرحبًا بك في عالم التفاصيل الأنيقة</h1>
          <p>نؤمن أن الجمال يسكن التفاصيل الصغيرة</p>
          <p>هنا ستجد تحفًا وديكور يناسب ذوقك الرفيع، مزيج فريد من الأناقة الكلاسيكية وروح العصرية في آن واحد</p>
          <div class="btns">
            <button class="btn-primary">التسوق الآن</button>
            <button class="btn-secondary">استكشف المزيد</button>
          </div>
        </div>

        <div class="counter">
          <div><span>+64</span><p>سنة خبرة</p></div>
          <div><span>481+</span><p>منتج حصري</p></div>
          <div><span>45K+</span><p>عميل سعيد</p></div>
          <div><span>145+</span><p>مدينة نوصلها</p></div>
        </div>
      </div>
    </section>

    <!-- Featured Products -->
    <section>
      <div class="container">
        <h2 class="section-title">أحدث المنتجات</h2>
        <div class="products-grid">
          <div class="product-card" v-for="n in 8" :key="n">
            <img src="https://arkan.sa/cdn/shop/products/1.jpg" alt="منتج">
            <div class="info">
              <h3>طاولة جانبية فخمة</h3>
              <p class="price">1,100 ر.س</p>
              <p class="old-price">1,600 ر.س</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Instagram Gallery -->
    <section style="background:#0f0606;">
      <div class="container">
        <h2 class="section-title">تابعونا على إنستقرام</h2>
        <p style="text-align:center;margin-bottom:40px;color:#ccc;">@arkan_decor</p>
        <div class="gallery">
          <img v-for="i in 9" :key="i" src="https://arkan.sa/cdn/shop/files/insta1.jpg" style="border-radius:15px;">
        </div>
      </div>
    </section>

    <!-- Features -->
    <section>
      <div class="container">
        <h2 class="section-title">لماذا تختار أركان؟</h2>
        <div class="features">
          <div class="feature-box">
            <h3>توصيل سريع وآمن</h3>
            <p>نصلك خلال 3-7 أيام في كل مدن المملكة</p>
          </div>
          <div class="feature-box">
            <h3>ضمان جودة 100%</h3>
            <p>استرجاع مجاني خلال 14 يوم</p>
          </div>
          <div class="feature-box">
            <h3>دفع عند الاستلام</h3>
            <p>ادفع نقداً أو بالبطاقة عند الاستلام</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer>
      <div class="container">
        <div class="logo">أركان</div>
        <p>متجر ديكور فخم يقدم أرقى القطع المنزلية</p>
        <div class="socials">
          <a href="#">Instagram</a>
          <a href="#">WhatsApp</a>
          <a href="#">Snapchat</a>
        </div>
        <p style="margin-top:40px;opacity:0.6;">© 2025 أركان - جميع الحقوق محفوظة</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import './assets/style.css'

onMounted(() => {
  document.querySelectorAll('.product-card').forEach((card, i) => {
    card.style.animationDelay = `${i * 0.1}s`
    card.classList.add('fade-up')
  })
})
</script>

<style scoped>
.fade-up { opacity:0; transform:translateY(50px); animation:fadeUp 0.8s forwards; }
@keyframes fadeUp { to { opacity:1; transform:translateY(0); } }
</style>