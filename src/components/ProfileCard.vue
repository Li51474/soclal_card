<template>
  <div
    class="profile-card"
    :class="[themeClass]"
  >
    <!-- 头像与基本信息 -->
    <div class="avatar-section">
      <img
        src="../assets/xiantiaodog.jpg"  
        alt="头像"
        class="avatar"
      />
    </div>

    <!-- 切换主题按钮 -->
    <button @click="$emit('toggle-theme')">
      切换主题
    </button>
  </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  theme: String
});

// 根据主题切换样式类
const themeClass = computed(() => ({
  'theme-purple': props.theme === 'purple',
  'theme-green': props.theme === 'green'
}));
</script>

<style scoped>
.profile-card {
  width: 300px;
  padding: 20px;
  border-radius: 15px;
  transition: all 0.3s;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1); /* 增加阴影 */
  background-color: white; /* 默认背景 */
  color: #333;
}

.theme-purple {
  background: linear-gradient(135deg, #ff4d4f 0%, #f89583 100%);
  color: white;
}

.theme-green {
  background: linear-gradient(135deg, #00b09b 0%, #96c93d 100%);
  color: white;
}

.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 15px;
}

button {
  margin-top: 15px;
  padding: 10px 20px;
  border: none;
  border-radius: 25px;
  cursor: pointer;
  font-size: 1em;
  transition: background-color 0.3s;
  background-color: #ff7043; /* 初始按钮颜色 */
  color: white;
}

button:hover {
  background-color: #ff5722; /* 悬停时按钮颜色 */
}
.profile-card {
  position: relative;
  animation: slideRight 2s ease-in-out forwards;
}
@keyframes slideRight {
  0% {
    left: -100%; /* 从屏幕外左侧开始 */
  }
  100% {
    left: 0; /* 移动到原始位置 */
  }
}

</style>
