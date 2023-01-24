<template>
    <div>
        <img :src=card.imageUrl alt="" @click.self="rotate()" :class="isTapped ? 'rotate-12' : 'rotate-0'" class="p-4">
    </div>
</template>

<script>
export default {
    name: "CardComponent",
    props: ['card'],
    data(){
        return {
            isTapped: false
        }
    },
    methods: {
        rotate(){
            this.isTapped = !this.isTapped
        }
    }
    
}


</script>