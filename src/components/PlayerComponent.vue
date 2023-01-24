<template>
    <div>Player</div>
    <input type="text" v-model="cardSearch" class="border-2 border-black" placeholder="Search Cards Here" @keyup.enter="findCard"/>
    <div>
        <button class="mx-2 border border-black px-3 py-1 rounded-md my-4" @click="getLand('forest')">Forest</button>
        <button class="mx-2 border border-black px-3 py-1 rounded-md my-4" @click="getLand('swamp')">Swamp</button>
        <button class="mx-2 border border-black px-3 py-1 rounded-md my-4" @click="getLand('island')">Island</button>
        <button class="mx-2 border border-black px-3 py-1 rounded-md my-4" @click="getLand('plains')">Plains</button>
        <button class="mx-2 border border-black px-3 py-1 rounded-md my-4" @click="getLand('mountain')">Mountain</button>
    </div>
    <div class="flex flex-col pb-6 place-content-center border border-black">
        <h2 class="text-center">Creatures</h2>
        <div class="flex flex-row flex-wrap place-content-center">
            <CardComponent v-bind:card="card" v-for="card in creatureCards" :key="card.multiverseid" />
        </div>
    </div>
    <div class="flex flex-col pb-6 place-content-center place-items-center">
        <h2>Land</h2>
        <div class="flex flex-row flex-wrap place-items-center">
            <CardComponent v-bind:card="card" v-for="card in landCards" :key="card.multiverseid" />
        </div>
    </div>

</template>

<script>
import CardComponent from "./CardComponent.vue"

export default {
    name: 'PlayerComponent',
    components: {
        CardComponent
    },
    data(){
        return {
            creatureCards : [],
            landCards : [],
            cardObject : [],
            cardSearch : '',
            isTapped : false,
            index : 1
        }
    },
    methods:{
    findCard(){
        const url = `https://api.magicthegathering.io/v1/cards?name=${this.cardSearch}`
        fetch(url)
            .then(res => res.json())
            .then(data => {
                this.cardObject = (data.cards[0])
                if (this.cardObject.type != 'Land'){
                    this.creatureCards.push(this.cardObject)
                } else {
                    this.landCards.push(this.cardObject)
                }
            })
        this.index = this.index + 1
        this.cardSearch = ''
    },

    getLand(land){
        const url = `https://api.magicthegathering.io/v1/cards?type=${land}`
        fetch(url)
            .then(res => res.json())
            .then(data => {
                this.cardObject = (data.cards[0])
                this.landCards.push(this.cardObject)
            })
    },
    rotate(){
        this.isTapped = !this.isTapped
    }
}
}


</script>