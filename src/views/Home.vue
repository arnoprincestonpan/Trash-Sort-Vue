<template>
    <div class="container-fluid">
        <Parts></Parts>
        <div class="w-100 d-flex flex-row flex-wrap ">
            <Bin class="col-md-3"></Bin>
            <Bin class="col-md-3"></Bin>
            <Bin class="col-md-3"></Bin>
            <Bin class="col-md-3"></Bin>
        </div>
    </div>
</template>
<script setup>
import Parts from '@/components/Parts.vue'
import Bin from '@/components/Bin.vue'
</script>