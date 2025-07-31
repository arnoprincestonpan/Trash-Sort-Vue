<template>
  <div class="d-flex flex-column min-vh-100">
    <Header>
    </Header>
    <Home></Home>
    <Footer>
    </Footer>
  </div>
</template>
<script setup>
import Header from '@/components/layout/Header.vue'
import Footer from '@/components/layout/Footer.vue'
import Home from '@/views/Home.vue'
</script>
<style scoped></style>
