<template>
    <img class="avatar rounded-full m-4 w-8 ml-2 mb-0 mt-0" :src="src" />
</template>
  
<script>
  export default {
    props: { src: { type: String, default: '' } }
  }
</script>