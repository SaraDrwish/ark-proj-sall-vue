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

.hero-section {
    padding: 80px 0;
    // استخدام تدرج لوني عميق للخلفية
    background-image: linear-gradient(135deg, $dark-primary 0%, $dark-secondary 100%);
    position: relative;
    overflow: hidden;
}

.hero-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    text-align: right;
    
    @media (max-width: 768px) {
        flex-direction: column;
        text-align: center;
    }
}

.main-title {
    font-size: 3.5rem;
    margin-bottom: 20px;
    
    @media (max-width: 768px) {
        font-size: 2.5rem;
    }
}

.subtitle {
    font-size: 1.2rem;
    line-height: 1.8;
    margin-bottom: 40px;
}

.action-buttons {
    display: flex;
    gap: 20px;
    
    @media (max-width: 768px) {
        justify-content: center;
        width: 100%;
    }
}

.btn {
    padding: 15px 30px;
    border: 2px solid;
    border-radius: 4px;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s;
}

.primary-btn {
    background-color: $accent-color;
    color: $dark-primary;
    border-color: $accent-color;
    &:hover {
        background-color: darken($accent-color, 10%);
        border-color: darken($accent-color, 10%);
    }
}

.secondary-btn {
    background: none;
    color: $light-text;
    border-color: $light-text;
    &:hover {
        background-color: rgba(255, 255, 255, 0.1);
    }
}

.stats-bar {
    display: flex;
    justify-content: space-around;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.3); // خلفية شفافة تبرز الإحصائيات
    border-radius: 8px;
    padding: 20px;
    margin-top: 50px;
    
    @media (max-width: 600px) {
        flex-wrap: wrap;
        gap: 20px;
    }
}

.stat-item {
    text-align: center;
    .stat-number {
        display: block;
        font-size: 2.5rem;
        font-weight: 900;
        color: $accent-color;
    }
    .stat-label {
        font-size: 1rem;
        color: rgba(255, 255, 255, 0.8);
    }
}
</style>