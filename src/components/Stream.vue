<script setup>
import Tweet from "@/components/Tweet.vue";

const tweets = Array.from({ length: 9 }, (_, i) => ({
  id: i + 1,
  author: 'Franzi Musterfrau',
  timestamp: 'vor 1 Minute',
  text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nunc ut aliquam tincidunt...',
  avatar: `https://i.pravatar.cc/100?u=${i + 1}`
}))
</script>

<template>
  <section class="stream">
    <Tweet
        v-for="tweet in tweets"
        :key="tweet.id"
        :author="tweet.author"
        :timestamp="tweet.timestamp"
        :text="tweet.text"
        :avatar="tweet.avatar"
    />        </section>
</template>

<style scoped>

</style>