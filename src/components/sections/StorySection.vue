<template>
  <section class="story-section">
    <div class="content-container">
      <div class="text-content">
        <h2 class="title">رحلة اركان عبر الزمن</h2>
        <p class="description">
          بدأت قصة اركان في عام 1995... نحن نفخر بالحفاظ على الوصفات الأصيلة مع إضافة لمسات عصرية تناسب أذواق جيل اليوم. [cite: 80, 81]
        </p>
        <button class="read-more-btn">
          اقرأ قصتنا الكاملة -
        </button>
      </div>
      </div>
  </section>
</template>

<style lang="scss" scoped>

 @import "../../assets/styles/_variables.scss";

.story-section {
    padding: 80px 0;
    
    // التدرج اللوني المطابق للتصميم 
    background-image: linear-gradient(to right, $dark-primary, $dark-secondary);
    color: $light-text;
}

.content-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;

    // Media Query: لترتيب العناصر عمودياً على الجوال (التجاوبية)
    @media (max-width: 900px) {
        flex-direction: column;
        text-align: center;
    }
}

.title {
    font-size: 2.5rem;
    margin-bottom: 20px;
}

.description {
    font-size: 1.1rem;
    line-height: 1.6;
    margin-bottom: 30px;
}

.read-more-btn {
    padding: 12px 25px;
    background: $accent-color;
    color: $dark-primary;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
}
</style>