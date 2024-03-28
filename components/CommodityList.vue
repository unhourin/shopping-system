<template>
  <div class="container">
    <h1 class="my-4">商品列表</h1>
    <div class="row">
      <div class="col-md-4" v-for="things in thingsList" :key="things.id" style="margin-bottom: 20px;">
        <div class="card h-100">
          <img :src="things.imageSrc" class="card-img-top" alt="Product Image">
          <div class="card-body d-flex flex-column justify-content-between">
            <div>
              <h5 class="card-title">{{ things.name }}</h5>
              <p class="card-text">{{ things.description }}</p>
            </div>
            <div class="mt-2">
              <p class="card-text">价格: {{ things.price }}</p>
              <button class="btn btn-primary btn-sm" @click="addToCart(things.id)">ショッピングカートに追加</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import axiosInstance from '~/utils/request';

const thingsList = ref(null);
const route = useRoute(); // 使用 useRoute 获取当前路由信息

onMounted(async () => {
  try {
    // 获取 userId 参数
    const userId = route.value.params.userId;

    // 发送请求获取数据
    const response = await axiosInstance.get(`/things/${userId}`);
    const newThingsList = response.data;

    // 处理数据
    newThingsList.forEach(item => {
      item.imageSrc = `http://localhost:8080/${item.cover}`;
    });

    // 更新 thingsList
    thingsList.value = newThingsList;
  } catch (error) {
    console.error(error);
  }
});

const addToCart = async (id: number) => {
  try {
    // 在此处您可以使用 userId 参数
    const userId = route.value.params.userId;

    // 构造请求参数
    const param = {
      thingsId: id,
      userId: userId // 将 userId 添加到请求中
    };

    // 发送请求
    const response = await axiosInstance.post('/add-to-cart', param);

    // 处理响应
    console.log(response.data);
  } catch (error) {
    console.error(error);
  }
}
</script>


<style scoped>
.card {
  border: 1px solid #dee2e6;
  border-radius: 0.25rem;
  transition: box-shadow 0.3s ease;
}

.card:hover {
  box-shadow: 0 0.25rem 0.75rem rgba(0, 0, 0, 0.1);
}

.card-img-top {
  height: 200px; /* 调整图片高度 */
  object-fit: cover; /* 图片尺寸不变，填充整个容器 */
}

.btn-primary {
  font-size: 14px; /* 调整按钮字体大小 */
}
</style>
