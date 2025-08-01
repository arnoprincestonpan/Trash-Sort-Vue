<template>
    <div class="container-fluid">
        <Parts></Parts>
        <div class="w-100 d-flex flex-row flex-wrap ">
            <Bins></Bins>
        </div>
    </div>
</template>
<script setup>
import Parts from '@/components/Parts.vue'
import Bin from '@/components/Bin.vue'
import Bins from '@/components/Bins.vue'
</script>