<template>
  <div class="postcard-container">
    <ProfileCard
      :user="userData"
      :theme="currentTheme"
      @toggle-theme="toggleTheme"
      :key="currentTheme"  
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ProfileCard from './components/ProfileCard.vue';

// 响应式用户数据
const userData = ref({
  name: '哪吒',
  job: '神话英雄',
  bio: '三头六臂，风火轮，乾坤圈',
  skills: ['风火轮', '乾坤圈', '三头六臂', '混天绫'],
  contact: 'contact@example.com'
});

// 切换主题颜色
const currentTheme = ref('purple');
const toggleTheme = () => {
  currentTheme.value = currentTheme.value === 'purple' ? 'green' : 'purple';
};
</script>

<style scoped>
.postcard-container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(45deg, #ffecd2 0%, #fcb69f 100%); /* 明信片风格背景 */
}

.ProfileCard {
  width: 350px;
  height: 450px;
  padding: 20px;
  border-radius: 15px;
  background-color: #fff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* 卡片阴影效果 */
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  animation: slideRight 1s ease-out forwards;
}

@keyframes slideRight {
  0% {
    transform: translateX(-100%); /* 从屏幕外左侧开始 */
  }
  100% {
    transform: translateX(0); /* 移动到原来的位置 */
  }
}

.ProfileCard .header {
  text-align: center;
  margin-bottom: 15px;
}

.ProfileCard .name {
  font-size: 1.5em;
  font-weight: bold;
  color: #4a4a4a;
}

.ProfileCard .job {
  font-size: 1.2em;
  color: #9b9b9b;
}

.ProfileCard .bio {
  font-size: 1em;
  color: #555;
  margin-top: 10px;
}

.ProfileCard .skills {
  list-style-type: none;
  padding: 0;
  font-size: 0.9em;
  color: #777;
}

.ProfileCard .skills li {
  margin: 5px 0;
}

.ProfileCard .contact {
  font-size: 0.9em;
  color: #777;
  margin-top: 15px;
  text-align: center;
}

button {
  background-color: #ff7043;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  margin-top: 10px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #ff5722;
}
</style>
