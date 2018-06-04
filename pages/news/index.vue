<template>
    <p>{{ params }}</p>
</template>

<script>
  import { fileMap, sourceFileArray } from '@/posts/json/summary.json';
    export default {
      asyncData({params}) {
        console.log(sourceFileArray);
        return Object.assign({}, sourceFileArray, {params});
      }
    }
</script>

<style scoped>

</style>
