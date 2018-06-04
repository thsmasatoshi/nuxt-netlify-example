<template>
  <div>
    <h1>{{ title }}</h1>
    <div class="post-meta">
      <time>{{ params.date }}</time>
    </div>
    <div v-html="bodyHtml"></div>
  </div>
</template>
<script>
  import {sourceFileArray} from '@/posts/json/summary.json';

  export default {
    validate({params}) {
      return sourceFileArray.includes(`contents/${params.date}-${params.slug}.md`);
    },
    asyncData({params}) {
        return Object.assign({}, require(`~/posts/json/${params.date}-${params.slug}.json`), {params});
    },
    head() {
      const title = `${this.title} - jmblog.jp`;
      const url = `https://jmblog.jp/posts/${this.params.date}/${this.params.slug}/`;
      return {
        title: title,
        link: [{rel: 'canonical', href: url}],
      };
    },
  };
</script>

<style scoped>

</style>
