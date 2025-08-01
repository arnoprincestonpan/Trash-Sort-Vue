<template>
    <div class="border rounded p-1 mt-2 mb-1">
        <h2>Parts</h2>
        <div class="text-center">
            <figure class="figure">
                <img :src="parts[current].source || noImage" class="figure-img img-fluid rounded" style="max-width: 300px;">
                <figcaption class="figure-caption">{{parts[current].alternative }}</figcaption>
            </figure>
        </div>
        <p class="text-center">Select the proper container where the part should be placed.</p>
        <div class="p-3 gap-1 d-flex justify-content-center flex-wrap flex-row">
            <button @click="handleBinSelection(type.name)" v-for="type in binType" :class="type.buttonColor" class="border col-sm">{{ type.name }}</button>
            <button @click="handleNextButton" class="btn btn-danger border">Next</button>
        </div>
    </div>
</template>
<script setup>
import { reactive, ref } from 'vue'
import { BINTYPES } from '@/constants/bins'
import noImage from '../../public/images/no-image.png'
import newspaper from '../../public/images/part-1.png'
const parts =
    [
        {
            name: "Newspaper",
            source: newspaper,
            alternative: "Newspaper",
            bin: BINTYPES.PAPER,
        },
        {
            name: "Aluminum Can",
            source: "You don't have to worry",
            alternative: "Aluminum Can",
            bin: BINTYPES.CONTAINERS,
        },
        {
            name: "Plastic Yogurt Container",
            source: "You don't have to worry",
            alternative: "Plastic Yogurt Container",
            bin: BINTYPES.CONTAINERS,
        },
        {
            name: "Glass Jar (empty & clean)",
            source: "You don't have to worry",
            alternative: "Glass Jar",
            bin: BINTYPES.GLASS,
        },
        {
            name: "Magazines",
            source: "You don't have to worry",
            alternative: "Magazine",
            bin: BINTYPES.PAPER,
        },
        {
            name: "Steel Food Can",
            source: "You don't have to worry",
            alternative: "Steel Food Can",
            bin: BINTYPES.CONTAINERS,
        },
        {
            name: "Old Cell Phone",
            source: "You don't have to worry",
            alternative: "Old Cell Phone",
            bin: BINTYPES.DEPOT,
        },
        {
            name: "Plastic Grocery Bag",
            source: "You don't have to worry",
            alternative: "Plastic Grocery Bag",
            bin: BINTYPES.DEPOT,
        },
        {
            name: "Broken Television",
            source: "You don't have to worry",
            alternative: "Broken Television",
            bin: BINTYPES.DEPOT,
        },
        {
            name: "Egg Cartons (cardboard)",
            source: "You don't have to worry",
            alternative: "Egg Cartons",
            bin: BINTYPES.PAPER,
        },
        {
            name: "Half Eaten Chicken Leg",
            source: "",
            alternative: "Half Eaten Chicken Leg",
            bin: BINTYPES.COMPOST,
        },
        {
            name: "Used Tea Bags",
            source: "",
            alternative: "Used Tea Bags",
            bin: BINTYPES.COMPOST,
        }
    ]

const current = ref(0)
const selections = ref([parts.length])
const selected = ref("")

const handleBinSelection = (selection) => {
    console.log("Number of Selections: ", parts.length)
    console.log(`Clicked:`, selection)
    selected.value = selection
}

const handleNextButton = () => {
    if(selected.value === "")return
    console.log('Selection:', selected.value)
    selections.value[current] = selected.value
    console.log(`Selections at Array: ${selections.value[current]}`)
}

const binType = [
    {
        name: "paper",
        buttonColor: "btn btn-warning",
    },
    {
        name: "container",
        buttonColor: "btn btn-primary",
    },
    {
        name: "glass",
        buttonColor: "btn btn-secondary",
    },
    {
        name: "trash",
        buttonColor: "btn btn-dark",
    },
    {
        name: "compost",
        buttonColor: "btn btn-success",
    },
    {
        name: "depot",
        buttonColor: "btn btn-light",
    },
]
</script>