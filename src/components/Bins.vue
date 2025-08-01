<template>
    <div class="card-group">
        <Bin v-for="info in binInformation"
            :key="info.title" :source="info.source || IMAGESOURCE.NOIMAGE"
            :alternative="info.alternative"
            :title="info.title.charAt(0).toUpperCase() + info.title.slice(1).toLowerCase()"
            :description="info.description"
            class="flex-fill"
        ></Bin>
    </div>
</template>
<script setup>
import Bin from './Bin.vue';
import { BINTYPES } from '@/constants/bins';
import { BINIMAGES } from '@/constants/images';

const binInformation = [
    {
        source: BINIMAGES.PAPER,
        alternative: "",
        title: BINTYPES.PAPER,
        description: "Paper bins take all sort of papers. This includes paper containers. All paper, including cardboard must be flattened before being placed into the bin.",
    },
    {
        source: BINIMAGES.CONTAINER,
        alternative: "",
        title: BINTYPES.CONTAINERS,
        description: "Container bins take all sorts of containers. From plastic lids, pumps and caps, to metal, foil containers. These bins do not take glass containers.",
    },
    {
        source: BINIMAGES.GLASS,
        alternative: "",
        title: BINTYPES.GLASS,
        description: "Glass bins are very niche. They only take glass. This includes wine glass bottles to masonary glass jars. These bins do not take non-glass containers.",
    },
    {
        source: BINIMAGES.COMPOST,
        alternative: "",
        title: BINTYPES.COMPOST,
        description: "Compost bins take everything that is compostable. All unfinished food and food scraps can go in here. These bins do not take in any non-biodegrable items.",
    },
    {
        source: BINIMAGES.DEPORT,
        alternative: "",
        title: BINTYPES.DEPOT,
        description: "There are multiple depots in the city that accept all other items. These include complex items like electronics. Please research each depot for items accepted.",
    },
    {
        source: BINIMAGES.TRASH,
        alternative: "",
        title: BINTYPES.TRASH,
        description: "Trash bins take garbage. Plastics that are not recyclable (see the # underneath and check wtih your city). Broken glass or small items usually go in here.",
    },
]
</script>