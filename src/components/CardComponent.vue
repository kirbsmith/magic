<template>
    <div class="w-48" :class="{'hidden' : isDestroyed}">
        <img :src=card.imageUrl alt="" @click.self="rotate()" :class="{ 'rotate-12': isTapped, 'grayscale opacity-40 duration-1000': isDisabled }"  class="p-4">
        <button class="text-center border border-black rounded-lg px-2 hover:bg-gray-800 hover:text-gray-200 duration-300" @click="disableCard()" v-if="!isDisabled">Send to graveyard</button>
        <button class="text-center border border-black rounded-lg px-2 hover:bg-gray-800 hover:text-gray-200 duration-300" @click="disableCard()" v-else>Return from graveyard</button>
        <button v-if="!isDestroyed" class="text-center border border-black rounded-lg px-2 hover:bg-red-800 hover:text-gray-300 duration-300 my-2" @click="exileCard()">Exile Card</button>
    </div>
    <div>
        <button class="text-center border border-black rounded-lg px-2 hover:bg-red-800 hover:text-gray-300 duration-300 my-2" v-if="isDestroyed" @click="exileCard()">Bring {{ card.name }} back</button>
    </div>
</template>

<script>
export default {
    name: "CardComponent",
    props: ['card'],
    data(){
        return {
            isTapped: false,
            isDisabled: false,
            isDestroyed: false
        }
    },
    methods: {
        rotate(){
            this.isTapped = !this.isTapped
        },
        disableCard(){
            this.isDisabled = !this.isDisabled
        },
        exileCard(){
            this.isDestroyed = !this.isDestroyed
        }

    }
    
}


</script>