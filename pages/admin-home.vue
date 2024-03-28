<template>
  <div class="app">
    <!-- 导航栏 -->
    <header class="navbar">
      <!-- 导航栏内容 -->
      <nav>
        <!-- 导航链接 -->
        <ul>
          <li><a href="#">Home</a></li>
          <li><a href="#">About</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </nav>
    </header>

    <!-- 主体内容 -->
    <main class="main">
      <!-- 左侧菜单 -->
      <aside class="sidebar">
        <!-- 菜单内容 -->
        <ul>
          <li><a href="#">Menu Item 1</a></li>
          <li><a href="#">Menu Item 2</a></li>
          <li><a href="#">Menu Item 3</a></li>
        </ul>
      </aside>

      <!-- 主体右边内容 -->
      <div class="content">
        <!-- 主体内容区域 -->
        <div class="main-content">
          <!-- 主体内容内容 -->
          <h1>Main Content</h1>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed vitae est vel nulla condimentum suscipit.</p>
          <!-- 主体内容过长时可以滚动 -->
          <div class="scrollable">
            <!-- 内容列表 -->
            <ul>
              <li>Item 1</li>
              <li>Item 2</li>
              <li>Item 3</li>
              <!-- 更多内容 -->
            </ul>
          </div>
        </div>
      </div>
    </main>

    <!-- 底部信息 -->
    <footer class="footer">
      <!-- 底部内容 -->
      <p>&copy; 2024 Your Website</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
/* 全局样式 */
body, html {
  margin: 0;
  padding: 0;
}

/* 整体布局样式 */
.app {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

/* 导航栏样式 */
.navbar {
  background-color: #333;
  color: #fff;
  padding: 10px 20px;
}

.navbar nav ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.navbar nav ul li {
  display: inline;
  margin-right: 20px;
}

.navbar nav ul li a {
  color: #fff;
  text-decoration: none;
}

/* 主体布局样式 */
.main {
  display: flex;
  flex: 1;
}

/* 左侧菜单样式 */
.sidebar {
  background-color: #f4f4f4;
  width: 200px;
  padding: 20px;
}

.sidebar ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.sidebar ul li {
  margin-bottom: 10px;
}

.sidebar ul li a {
  color: #333;
  text-decoration: none;
}

/* 主体右边内容样式 */
.content {
  flex: 1;
  padding: 20px;
}

/* 主体内容过长时可滚动样式 */
.scrollable {
  overflow-y: auto;
  max-height: calc(100vh - 200px); /* 根据实际高度调整 */
}

/* 底部信息样式 */
.footer {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 10px 0;
}
</style>
