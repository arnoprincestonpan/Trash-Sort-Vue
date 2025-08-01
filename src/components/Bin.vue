<template>
  <div class="card col-lg-4 col-md-6 col-sm-6 d-flex flex-column">
    <img :src="source" class="card-img-top" :alt="alternative"/>
    <div class="card-body">
      <h5 class="card-title">{{ title }}</h5>
      <p class="card-text">{{ description }}</p>
      <p class="card-text"><small class="text-body-secondary"><a href="https://www.recyclebc.ca">More Info at RecycleBC.ca</a></small></p>
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