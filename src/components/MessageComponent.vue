<template>
  <div class="message m-3">
    <div class="flex place-items-center" :class="sender ? 'flex-row-reverse' : ''">
      <AvatarComponent v-if="sender" :src="photoUrl" />
      <span v-else>{{ name }}</span>
      <div class="text text-slate-200 w-3/4 rounded-lg py-2 break-words" :class="sender ? 'bg-green-800 text-left pl-3' : 'bg-gray-700 text-right pr-3'">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
import AvatarComponent from './AvatarComponent.vue'
export default {
  components: { AvatarComponent },
  props: {
    name: { type: String, default: '' },
    photoUrl: { type: String, default: '' },
    sender: { type: Boolean, default: false }
  }
}
</script>
  