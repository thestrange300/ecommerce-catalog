<script setup>
import { ref, onMounted, computed } from 'vue';
import '@/assets/style/ProductCard.css';

const index = ref(1);
const product = ref(null);
const loading = ref(true);

const categoryClass = computed(() => {
    if (!product.value) return "page-unavailable";
    switch (product.value.category) {
    case "men's clothing":
        return "page-men";
    case "women's clothing":
        return "page-women";
    default:
        return "";
    }
});

const fetchProduct = async () => {
    loading.value = true;
    const response = await fetch(`https://fakestoreapi.com/products/${index.value}`, {
        method: 'GET',
        mode: 'cors',
    });
    const data = await response.json();
    (data.category === "men's clothing" || data.category === "women's clothing") ? product.value = data : product.value = null;

    loading.value = false;
    (index.value === 20) ? index.value = 1 : index.value++;
}

onMounted(() => {
    fetchProduct();
});

</script>

<template>
<div class="main-container">
    <div class="bg" :class="categoryClass"></div>
        <div class="product-card" :class="categoryClass">
        <div v-if="loading">
        <div class="loader">
            <div class="spinner"></div>
        </div>
        </div>
        <div v-else-if="product && (product.category == 'men\'s clothing' || product.category == 'women\'s clothing')" class="grid-container">
            <div class="image-container">
                <img :src="product.image" alt="product image">
            </div>
            <div class="info-container">
                <div class="top-container">
                    <h1 class="title" :class="categoryClass">{{ product.title }}</h1>
                    <div class="category-container">
                            <p class="category">{{ product.category }}</p>
                        <div class="rating">
                                <span>{{ product.rating.rate }} / 5</span>
                                <span v-for="n in 5" :key="n" class="rating-dot" :class="[n <= Math.round(product.rating.rate) ? 'rating-filled' : 'rating-empty', categoryClass]"></span>
                        </div>
                    </div>
                    <p class="description">
                        {{ product.description }}
                    </p>
                </div>
                <div class="bot-container">
                    <p class="price" :class="categoryClass">$ {{ product.price.toFixed(2) }}</p>
                    <div class="button-container">
                        <button class="buy-btn" :class="categoryClass">Buy now</button>
                        <button @click="fetchProduct" class="next-btn">Next product</button>
                    </div>
                </div>
            </div>
        </div>
        <div class="unavailable-container" v-else>
            <h1 class="title page-unavailable">This product is unavailable to show</h1>
            <button @click="fetchProduct" class="next-btn">Next product</button>
        </div>
    </div>
</div>


</template>

