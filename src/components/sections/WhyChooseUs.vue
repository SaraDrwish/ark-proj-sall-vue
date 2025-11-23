<template>
  <section class="why-choose-us-section">
    <div class="container">
      <h2 class="section-title">لماذا تختار أركان؟</h2>
      <p class="subtitle">هنا، كل قطعة تحكي قصة... قصة ذوقك، وأناقتك، واهتمامك بكل ما هو جميل.</p>
      
      <div class="features-grid">
        <div v-for="(feature, index) in features" :key="index" class="feature-item">
          <span class="feature-icon">{{ feature.icon }}</span>
          <h3 class="feature-title">{{ feature.title }}</h3>
          <p class="feature-description">{{ feature.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'WhyChooseUs',
  data() {
    return {
      features: [
        {
          title: 'مكونات طبيعية 100%',
          description: 'نستخدم فقط أجود المكونات الطبيعية بدون أي إضافات صناعية أو مواد حافظة.',
          icon: '🌿' // مثال لأيقونة
        },
        {
          title: 'تحضير يومي طازج',
          description: 'نضمن وصول منتجاتنا إليك في قمة نضارتها وجودتها، مع تحضير يومي دقيق.',
          icon: '✨'
        },
        {
          title: 'ضمان استرجاع المال',
          description: 'إذا لم تكن راضياً تماماً، يمكنك استرجاع مبلغك بالكامل. ثقتكم هي أولويتنا.',
          icon: '💰'
        },
        {
          title: 'شحن سريع وموثوق',
          description: 'توصيل سريع ومدروس لجميع مناطق المملكة لضمان وصول طلبك في حالة ممتازة.',
          icon: '🚚'
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import '../../assets/styles/_variables.scss'; 

.why-choose-us-section {
  padding: 60px 0;
  // خلفية مختلفة قليلاً لتمييز القسم
  background-color: lighten($dark-primary, 5%); 
}

.section-title {
  font-size: 2.2rem;
  margin-bottom: 10px;
}

.subtitle {
  font-size: 1.1rem;
  color: rgba($light-text, 0.8);
  margin-bottom: 40px;
  text-align: center;
}

.features-grid {
  // استخدام CSS Grid لتنظيم المزايا
  display: grid;
  // عرض 4 أعمدة على الشاشات الكبيرة
  grid-template-columns: repeat(4, 1fr); 
  gap: 30px;
  text-align: center;

  // التجاوبية (Responsiveness)
  @media (max-width: 1024px) {
    // عرض عمودين على الأجهزة اللوحية
    grid-template-columns: repeat(2, 1fr); 
  }

  @media (max-width: 600px) {
    // عرض عمود واحد على الجوال
    grid-template-columns: 1fr; 
  }
}

.feature-item {
  padding: 20px;
  background-color: #3e161c; // خلفية البطاقة (مختلفة عن لون القسم)
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.4);
}

.feature-icon {
  font-size: 3rem;
  color: $accent-color; // لون التمييز للأيقونات
  display: block;
  margin-bottom: 15px;
}

.feature-title {
  font-size: 1.3rem;
  margin-bottom: 10px;
}

.feature-description {
  color: rgba($light-text, 0.7);
  font-size: 0.95rem;
  line-height: 1.6;
}
</style>