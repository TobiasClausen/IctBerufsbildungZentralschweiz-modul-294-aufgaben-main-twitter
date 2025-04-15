<script setup>
import { ref, onMounted } from 'vue'
import LoginInfo from '@/components/LoginInfo.vue'
import Composer from '@/components/Composer.vue'
import Tweet from '@/components/Tweet.vue'
import { fetchStream, checkAuth } from '../api/requests'
import { useAuth } from '../api/auth'

const { isLoggedIn } = useAuth()
const loading = ref(true)
const tweets = ref([])

async function loadTweets() {
  loading.value = true
  try {
    const stream = await fetchStream()
    tweets.value = stream
  } catch (error) {
    console.error(error)
  } finally {
    loading.value = false
  }
}

// Check auth status on mount
onMounted(async () => {
  const response = await checkAuth()
  console.log('checkAuth Resultat', response)
})

// Load tweets on mount and when new tweet is posted
onMounted(loadTweets)
</script>

<template>
  <div>
    <LoginInfo v-if="!isLoggedIn" />
    <Composer v-if="isLoggedIn" @posted="loadTweets" />
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


