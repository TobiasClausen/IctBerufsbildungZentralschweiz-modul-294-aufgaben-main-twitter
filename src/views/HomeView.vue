<script setup>
import { ref, onMounted } from 'vue'
import LoginInfo from '@/components/LoginInfo.vue'
import Composer from '@/components/Composer.vue'
import Tweet from '@/components/Tweet.vue'
import { fetchStream } from '../api/requests'

const loading = ref(true)
const tweets = ref([])

onMounted(async () => {
    loading.value = true
    try {
        const stream = await fetchStream()
        tweets.value = stream
    } catch (error) {
        console.error(error)
    } finally {
        loading.value = false
    }
})
</script>

<template>
  <div>
    <LoginInfo />
    <Composer />
    <div v-if="loading" class="loading">
      Lade Tweets...
    </div>
    <div v-else class="stream">
      <Tweet 
        v-for="tweet in tweets"
        :key="tweet.id"
        :user="tweet.user"
        :text="tweet.text"
        :created-at="tweet.createdAt"
      />
    </div>
  </div>
</template>


