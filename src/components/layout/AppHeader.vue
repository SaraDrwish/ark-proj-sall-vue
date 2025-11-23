<template>
  <header class="main-header">
    <div class="logo">Arkan أركان</div>
    
    <div class="search-bar">
      <input type="text" placeholder="ادخل كلمة البحث" class="search-input">
      <button class="search-icon">🔍</button>
    </div>

    <nav class="nav-links">
      <a href="#">المتجر</a>
      <a href="#">عروض</a>
      <a href="#">تخفيضات</a>
    </nav>
    
    <div class="user-actions">
      <button class="icon-btn">👤</button>
      <button class="icon-btn">🛒</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
};
</script>

<style lang="scss" scoped>
// يجب تصحيح المسار ليتناسب مع موقعه داخل مجلد layout
@import '../../assets/styles/_variables.scss'; 

.main-header {
  // تدرج لوني خفيف لتمييز الهيدر عن خلفية الصفحة الأساسية
  background-image: linear-gradient(to right, darken($dark-primary, 2%), $dark-secondary); 
  padding: 20px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top: 0;
  z-index: 100;

  // التجاوبية
  @media (max-width: 992px) {
    flex-wrap: wrap; // السماح للعناصر بالنزول لسطر جديد
  }
}

.logo {
  font-size: 1.8rem;
  font-weight: 800;
  color: $light-text;
  flex-shrink: 0;
}

.search-bar {
    display: flex;
    align-items: center;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    padding: 5px 15px;
    margin: 0 20px;
    flex-grow: 1;

    @media (max-width: 992px) {
        order: 3; // وضع شريط البحث في سطر جديد على الجوال
        width: 100%;
        margin: 15px 0;
    }
}

.search-input {
    background: none;
    border: none;
    color: $light-text;
    padding: 5px;
    width: 100%;
    &::placeholder {
        color: rgba(255, 255, 255, 0.7);
    }
    &:focus {
        outline: none;
    }
}

.search-icon {
    background: none;
    border: none;
    color: $light-text;
    cursor: pointer;
    font-size: 1.1rem;
}

.user-actions {
    display: flex;
    gap: 15px;
}

.icon-btn {
    background: none;
    border: none;
    color: $light-text;
    font-size: 1.5rem;
    cursor: pointer;
    transition: color 0.3s;
    &:hover {
        color: $accent-color;
    }
}
</style>