<template>
  <ul>
    <li v-for="article in articles" :key="article.slug">
      <nuxt-link :to="`/articles/${article.slug}`">
        {{ article.title }}
      </nuxt-link>
      <p>{{ article.updatedAt }}</p>
    </li>
  </ul>
</template>

<script lang="ts">
import { Context } from '@nuxt/types'

export default {
  async asyncData({ $content, params }: Context) {
    const articles = await $content('articles').fetch()
    return { articles }
  },
}
</script>
