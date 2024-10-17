<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/slide">Slide</RouterLink>
      </nav>
    </div>
  </header>

  <main>
    <RouterView />
  </main>
</template>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: #eeebeb;
  padding: 1rem;
  z-index: 1000;
}

body {
  margin: 0; /* Bỏ margin để không có khoảng cách ở xung quanh */
  padding-top: 5rem; /* Để nội dung không bị ẩn dưới thanh điều hướng */
}

main {
  display: flex; /* Sử dụng flexbox cho phần chính */
  justify-content: center; /* Căn giữa nội dung theo chiều ngang */
  align-items: center; /* Căn giữa nội dung theo chiều dọc */
  min-height: calc(100vh - 5rem); /* Chiều cao tối thiểu bằng chiều cao của viewport trừ chiều cao của header */
  padding: 1rem; /* Thêm padding nếu cần */
}

.wrapper {
  max-width: 1200px; /* Đặt chiều rộng tối đa cho wrapper */
  margin: 0 auto; /* Căn giữa wrapper */
}

nav {
  display: flex; 
  justify-content: center; 
  font-size: 12px; 
  margin-top: 0; 
}

nav a {
  padding: 0.5rem 1rem; 
  border-left: 1px solid var(--color-border); 
  text-decoration: none; 
  color: #333; 
  transition: background-color 0.3s; 
}

nav a:first-of-type {
  border: 0; 
}

nav a.router-link-exact-active {
  color: var(--color-text); 
  font-weight: bold; 
}

nav a:hover {
  background-color: #e0e0e0; 
}
</style>
