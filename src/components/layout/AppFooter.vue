<template>
  <footer class="main-footer">
    <div class="container">
      <p>&copy; {{ new Date().getFullYear() }} أركان. جميع الحقوق محفوظة.</p>
      <div class="footer-links">
        <a href="#">سياسة الخصوصية</a>
        <a href="#">الشروط والأحكام</a>
        <a href="#">تواصل معنا</a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter',
};
</script>

<style lang="scss" scoped>
@import '../../assets/styles/_variables.scss'; 

.main-footer {
  background-color: darken($dark-primary, 5%); // أغمق قليلاً من الخلفية الأساسية
  padding: 30px 0;
  color: $light-text;
  text-align: center;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: $max-width;
  margin: 0 auto;
  padding: 0 20px;
  
  @media (max-width: 600px) {
    flex-direction: column;
    gap: 15px;
  }
}

.footer-links a {
  color: $light-text;
  margin-right: 20px;
  text-decoration: none;
  &:hover {
    color: $accent-color;
  }
}
</style>