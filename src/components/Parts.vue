<template>
    <div class="border rounded p-1 mt-2 mb-1">
        <h2>Parts</h2>
        <div v-if="results !== ''">
            {{ results }}
        </div>
        <div class="text-center">
            <figure class="figure">
                <img :src="parts[current].source || NOIMAGE" class="figure-img img-fluid rounded" style="max-width: 300px;" :class="highlightImage">
                <figcaption class="figure-caption">{{parts[current].alternative }}</figcaption>
            </figure>
        </div>
        <p class="text-center">Select the proper container where the part should be placed.</p>
        <div class="p-3 gap-1 d-flex justify-content-center flex-wrap flex-row">
            <button @click="handleBinSelection(type.name)" v-for="type in binType" :class="type.buttonColor" class="border col-sm">{{ type.name }}</button>
            <button v-if="current < parts.length - 1" @click="handleNextButton" class="btn btn-danger border">Next</button>
            <button v-else @click="submit = !submit" class="btn btn-danger border">Submit</button>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue'
import { BINSTYLES, BINTYPES } from '@/constants/bins'
import { IMAGESOURCE, NOIMAGE } from '@/constants/images'
import { IMAGEHIGHLIGHTS } from '@/constants/imageHighlights'

const parts =
    [
        {
            name: "Newspaper",
            source: IMAGESOURCE.NEWSPAPER,
            alternative: "Newspaper",
            bin: BINTYPES.PAPER,
        },
        {
            name: "Aluminum Can",
            source: IMAGESOURCE.SODACAN,
            alternative: "Aluminum Can",
            bin: BINTYPES.CONTAINERS,
        },
        {
            name: "Plastic Yogurt Container",
            source: IMAGESOURCE.YOGURT,
            alternative: "Plastic Yogurt Container",
            bin: BINTYPES.CONTAINERS,
        },
        {
            name: "Glass Jar (empty & clean)",
            source: IMAGESOURCE.GLASSJAR,
            alternative: "Glass Jar",
            bin: BINTYPES.GLASS,
        },
        {
            name: "Magazines",
            source: IMAGESOURCE.MAGAZINE,
            alternative: "Magazine",
            bin: BINTYPES.PAPER,
        },
        {
            name: "Steel Food Can",
            source: IMAGESOURCE.TINCAN,
            alternative: "Steel Food Can",
            bin: BINTYPES.CONTAINERS,
        },
        {
            name: "Old Cell Phone",
            source: IMAGESOURCE.PHONE,
            alternative: "Old Cell Phone",
            bin: BINTYPES.DEPOT,
        },
        {
            name: "Plastic Grocery Bag",
            source: IMAGESOURCE.PLASTICBAG,
            alternative: "Plastic Grocery Bag",
            bin: BINTYPES.DEPOT,
        },
        {
            name: "Broken Television",
            source: IMAGESOURCE.BROKENTV,
            alternative: "Broken Television",
            bin: BINTYPES.DEPOT,
        },
        {
            name: "Egg Cartons (cardboard)",
            source: IMAGESOURCE.EMPTYCARTONPAPER,
            alternative: "Egg Cartons",
            bin: BINTYPES.PAPER,
        },
        {
            name: "Half Eaten Chicken Leg",
            source: IMAGESOURCE.HALFEATENDRUMSTICK,
            alternative: "Half Eaten Chicken Leg",
            bin: BINTYPES.COMPOST,
        },
        {
            name: "Used Tea Bags",
            source: IMAGESOURCE.USEDTEABAGS,
            alternative: "Used Tea Bags",
            bin: BINTYPES.COMPOST,
        }
    ]

const current = ref(0)
const selections = ref([parts.length])
const selected = ref("")
const highlightImage = ref(IMAGEHIGHLIGHTS.default.toString())
const submit = ref(false)
let results = ref("")


const handleBinSelection = (selection) => {
    console.log("Number of Selections: ", parts.length)
    console.log(`Clicked:`, selection)
    selected.value = selection
    handleImageHighlight()
}

const handleImageHighlight = () => {
    if(!selected.value || selected.value == undefined)return
    if(!IMAGEHIGHLIGHTS[selected.value])return
    console.log(IMAGEHIGHLIGHTS)
    console.log(IMAGEHIGHLIGHTS[selected.value])
    console.log(IMAGEHIGHLIGHTS[selected.value].toString())
    highlightImage.value = IMAGEHIGHLIGHTS[selected.value].toString()
}

const handleNextButton = () => {
    if((current.value - 1) >= selections.value)return
    if(selected.value === "")return
    console.log('Selection:', selected.value)
    selections.value[current.value] = selected.value
    console.log(`Selections at Array: ${selections.value[current.value]}`)
    current.value = current.value + 1
    console.log(`Current Selections Index ${current.value}`)
}

const handleResults = () => {
    results += ``
    let points = 0
    results += `<ul>`
    parts.map((part) => selections.value.map((selection, index) => {
        results += `<li>`
        if(selection.toString().toLowerCase() === part.toString().toLowerCase()){
            results += `CORRECT: ${++index}.): ${part.name.charAt(0).toUpperCase() + part.name.slice(1)} belongs in the ${BINTYPES.PAPER} bins.`
            points++
        }else {
            results += `INCORRECT: ${++index}.): ${part.name.charAt(0).toUpperCase() + part.name.slice(1)} belongs in the ${BINTYPES.PAPER} bins.`
        }
        results += `</li>`
    }))
    results += `</ul>`
}

const binType = [
    {
        name: BINTYPES.PAPER,
        buttonColor: BINSTYLES.PAPER
    },
    {
        name: BINTYPES.CONTAINERS,
        buttonColor: BINSTYLES.CONTAINERS,
    },
    {
        name: BINTYPES.GLASS,
        buttonColor: BINSTYLES.GLASS,
    },
    {
        name: BINTYPES.TRASH,
        buttonColor: BINSTYLES.TRASH,
    },
    {
        name: BINTYPES.COMPOST,
        buttonColor: BINSTYLES.COMPOST,
    },
    {
        name: BINTYPES.DEPOT,
        buttonColor: BINSTYLES.DEPOT,
    },
]
</script>