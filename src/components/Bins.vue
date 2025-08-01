<template>
    <Bin v-for="info in binInformation" :key="info"
    :source="info.source"
    :alternative="info.alternative"
    :title="info.title"
    :description="info.description"
    ></Bin>
</template>
<script setup>
import Bin from './Bin.vue';
import { BINTYPES } from '@/constants/bins';

const binInformation = [
    {
    source: "",
    alternative: "",
    title: BINTYPES.PAPER,
    description: "",
    },
    {
    source: "",
    alternative: "",
    title: BINTYPES.CONTAINERS,
    description: "",
    },
    {
    source: "",
    alternative: "",
    title: BINTYPES.GLASS,
    description: "",
    },
    {
    source: "",
    alternative: "",
    title: BINTYPES.COMPOST,
    description: "",
    },
    {
    source: "",
    alternative: "",
    title: BINTYPES.DEPOT,
    description: "",
    },
]
</script>