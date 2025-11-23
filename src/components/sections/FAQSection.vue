<template>
  <section class="faq-section">
    <div class="container">
      <h2 class="section-title">الأسئلة الشائعة</h2>
      <p class="subtitle">إجابات وافية لأكثر التساؤلات شيوعًا حول منتجاتنا وخدماتنا.</p>
      
      <div class="accordion-list">
        <div 
          v-for="(item, index) in faqItems" 
          :key="index" 
          class="accordion-item"
        >
          <div @click="toggleAnswer(index)" class="question-header">
            <h3 class="question-title">{{ item.question }}</h3>
            <span class="toggle-icon">{{ activeIndex === index ? '−' : '+' }}</span>
          </div>
          
          <transition name="accordion">
            <p v-if="activeIndex === index" class="answer-content">
              {{ item.answer }}
            </p>
          </transition>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'FAQSection',
  data() {
    return {
      activeIndex: null, // لتتبع فهرس السؤال المفتوح حاليًا
      faqItems: [
        {
          question: 'ما هي مدة صلاحية المنتجات؟',
          answer: 'نحن نضمن صلاحية جميع المنتجات لمدة 6 أشهر كحد أدنى من تاريخ الشراء، مع الالتزام بشروط التخزين المناسبة.'
        },
        {
          question: 'هل يمكنني استبدال أو استرجاع المنتجات؟',
          answer: 'نعم، يمكنك الاستبدال أو الاسترجاع خلال 7 أيام من تاريخ الاستلام، بشرط أن تكون المنتجات في حالتها الأصلية.'
        },
        {
          question: 'ما هي طرق الدفع المتاحة؟',
          answer: 'نقبل الدفع عبر البطاقات الائتمانية (فيزا وماستركارد)، مدى، الدفع عند الاستلام، والتحويل البنكي.'
        },
        {
          question: 'كم يستغرق الشحن والتوصيل؟',
          answer: 'يتم التوصيل داخل المدن الرئيسية خلال 2-4 أيام عمل، وللمناطق الأخرى قد يستغرق 5-7 أيام عمل.'
        }
      ]
    };
  },
  methods: {
    toggleAnswer(index) {
      // إذا كان السؤال المفتوح هو نفسه الذي تم النقر عليه، يتم إغلاقه (null)
      if (this.activeIndex === index) {
        this.activeIndex = null;
      } else {
        // وإلا، يتم فتح السؤال الجديد
        this.activeIndex = index;
      }
    }
  }
};
</script>


<style lang="scss" scoped>
// تصحيح مسار المتغيرات
@import '../../assets/styles/_variables.scss'; 

.faq-section {
  padding: 60px 0;
  // خلفية مختلفة قليلاً لتمييز القسم عن الأقسام المجاورة
  background-color: lighten($dark-primary, 3%); 
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

.accordion-list {
  max-width: 900px;
  margin: 0 auto;
}

.accordion-item {
  border: 1px solid rgba($light-text, 0.1);
  border-radius: 8px;
  margin-bottom: 15px;
  overflow: hidden;
  background-color: #3e161c; // خلفية بطاقة داكنة
  transition: all 0.3s ease;
  
  &:hover {
      box-shadow: 0 0 15px rgba($accent-color, 0.2);
  }
}

.question-header {
  padding: 18px 25px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  user-select: none;
  background-color: darken(#3e161c, 5%);
  transition: background-color 0.3s;
  
  &:hover {
      background-color: #4a1f26;
  }
}

.question-title {
  font-size: 1.1rem;
  font-weight: 500;
  margin: 0;
}

.toggle-icon {
  font-size: 1.5rem;
  font-weight: bold;
  color: $accent-color;
  transition: transform 0.3s;
  
  // لتدوير الأيقونة عند الفتح (لمسة جمالية)
  .accordion-item:not(.active) & {
      transform: rotate(45deg); 
  }
}

.answer-content {
  padding: 0 25px 18px;
  font-size: 1rem;
  color: rgba($light-text, 0.7);
  line-height: 1.7;
}

/* -------------------------------------- */
/* Vue Transition - للحركة السلسة */
/* -------------------------------------- */

.accordion-enter-active, .accordion-leave-active {
  transition: all 0.3s ease-out;
  max-height: 500px; /* يجب تعيين قيمة كبيرة هنا */
}

.accordion-enter-from, .accordion-leave-to {
  opacity: 0;
  max-height: 0;
  padding-top: 0;
  padding-bottom: 0;
}
</style>


