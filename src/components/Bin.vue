<template>
    <div class="card">
        <img :src="bin.source" class="card-img-top" :alt="bin.alternative">
        <div class="card-body">
            <h5 class="card-title">{{ bin.title }}</h5>
            <p class="card-text">{{ bin.description }}</p>
        </div>
    </div>
</template>
<script setup>
import { defineProps } from 'vue'
const bin = defineProps(
    {
        source: "",
        alternative: "",
        title: "",
        description: "",
    }
)

</script>