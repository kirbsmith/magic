<template>
    <div class="mb-2">
        <div v-if="isLogin" class="flex flex-row place-items-center  place-content-center">
            <AvatarComponent :src="user.photoURL"/>
            <button class="border-2 border-gray-800 bg-gray-800 px-4 py-1 rounded-md text-slate-300 hover:text-gray-800 hover:bg-slate-300 duration-300" @click="signOut">Sign Out</button>
        </div>
        <button v-else @click="signIn"  class="border-2 border-gray-800 bg-gray-800 px-4 py-1 rounded-md text-slate-300 hover:text-gray-800 hover:bg-slate-300 duration-300">Sign in</button>
    </div>
</template>

<script>
    import AvatarComponent from './AvatarComponent.vue'
    import { useAuth } from '@/firebase'

    export default {
        components: { AvatarComponent },
        setup(){
            const { user, isLogin, signOut, signIn } = useAuth()
            return { user, isLogin, signOut, signIn }
        }
    }

</script>