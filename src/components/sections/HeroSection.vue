<template>
  <section class="hero-section">
    <div class="hero-content container">
      <div class="text-side">
        <h1 class="main-title">مرحباً بك في عالم التفاصيل الأنيقة</h1>
        <p class="subtitle">
          تؤمن أن الجمال يسكن التفاصيل الصغيرة. هنا ستجد تحفاً وقطع ديكور فريدة تمتزج فيها الأناقة الكلاسيكية بروح العصرية الدافئة.
        </p>
        <div class="action-buttons">
          <button class="btn primary-btn">تسوق الآن</button>
          <button class="btn secondary-btn">اكتشف المزيد</button>
        </div>
      </div>
    </div>

    <div class="stats-bar container">
        <div class="stat-item">
            <span class="stat-number">45K+</span>
            <span class="stat-label">عميل سعيد</span>
        </div>
        <div class="stat-item">
            <span class="stat-number">481+</span>
            <span class="stat-label">نوع منتجات</span>
        </div>
        <div class="stat-item">
            <span class="stat-number">+64</span>
            <span class="stat-label">سنة خبرة</span>
        </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
};
</script>

<style lang="scss" scoped>
@import '../../assets/styles/_variables.scss'; 

// تعريف متغير لمسار الصورة لتكون ساعة القمر المضيئة (03da7890f3405e5df63cfebd14f0db0e.jpg)
$hero-image-path: '../../assets/imgs/03da7890f3405e5df63cfebd14f0db0e.jpg'; 

.hero-section {
    position: relative;
    overflow: hidden;
    min-height: 85vh; // ارتفاع مناسب لإظهار المحتوى والإحصائيات
    color: $light-text; // تحديد لون النص الأساسي ليكون فاتحاً
    display: flex;
    flex-direction: column;
    justify-content: space-between; // لدفع شريط الإحصائيات للأسفل
    
    // ⬅️ إنشاء طبقة Overlay (بدلاً من background-blend-mode)
    &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 1; // ليكون تحت النصوص
        
        // تدرج لوني داكن وقوي كـ Overlay (0.85 opacity) فوق الصورة
        background-image: 
            linear-gradient(rgba($dark-primary, 0.85), rgba($dark-primary, 0.85)), 
            url($hero-image-path);
            
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
    }
}

.hero-content {
    padding-top: 100px; 
    padding-bottom: 50px;
    z-index: 2; // التأكد من أن النص فوق الـ Overlay
    
    .text-side {
        max-width: 600px; // تحديد عرض جانب النص ليكون أكثر تركيزاً
        text-align: right;
        
        @media (max-width: 768px) {
            text-align: center;
            max-width: 100%;
        }
    }
}

.main-title {
    font-size: 3.5rem;
    line-height: 1.3;
    margin-bottom: 20px;
    color: $accent-color; // استخدام اللون الذهبي للعنون
    
    @media (max-width: 768px) {
        font-size: 2.5rem;
    }
}

.subtitle {
    font-size: 1.25rem;
    margin-bottom: 30px;
    color: rgba($light-text, 0.9);
}

.action-buttons {
    display: flex;
    gap: 15px;
    
    @media (max-width: 768px) {
        justify-content: center;
    }
    
    .btn {
        padding: 12px 30px;
        border: none;
        border-radius: 40px;
        font-size: 1rem;
        cursor: pointer;
        font-weight: bold;
        transition: transform 0.2s;
        
        &:hover {
            transform: translateY(-2px);
        }
    }
    
    .primary-btn {
        background-color: $accent-color;
        color: $dark-primary;
    }
    
    .secondary-btn {
        background-color: transparent;
        color: $light-text;
        border: 2px solid $light-text;
    }
}

/* -------------------- شريط الإحصائيات -------------------- */

.stats-bar {
    z-index: 2; 
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 40px;
    border-top: 1px solid rgba($light-text, 0.1);
    
    .stat-item {
        text-align: center;
        width: 8rem;
        height: 8rem;
        border:0.02rem solid $accent-color ;
        padding: 2rem;
        border-radius: 11rem;
        margin: 1rem ;
        gap:2rem;
    }
    
    .stat-number {
        font-size: 2rem;
        font-weight: bold;
        color: $accent-color;
        display: block;
        
        @media (max-width: 768px) {
            font-size: 2rem;
        }
    }
    
    .stat-label {
        font-size: 1rem;
        color: rgba($light-text, 0.7);
    }
    
    @media (max-width: 768px) {
        flex-wrap: wrap;
        gap: 20px;
        justify-content: space-around;
    }
}
</style>