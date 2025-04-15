<script setup>
defineProps({
  author: String,
  timestamp: String,
  text: String,
  avatar: String
})
</script>

<template>
  <div class="tweet">
    <div class="tweet__avatar">
      <img :src="avatar" alt="Avatar" />
    </div>
    <div class="tweet__content">
      <div class="tweet__header">
        <span class="tweet__author">{{ author }}</span>
        <span class="tweet__timestamp">{{ timestamp }}</span>
      </div>
      <div class="tweet__text">
        {{ text }}
      </div>
    </div>
  </div>
</template>

<style scoped>
/* (CSS bleibt unverändert wie oben) */
.tweet {
  display: flex;
  padding: 20px;
}

.tweet + .tweet {
  border-top: 1px solid #1e293b;
}

.tweet:last-child {
  border-bottom: 1px solid #1e293b;
}

.tweet__avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  overflow: hidden;
  margin-right: 20px;
}

.tweet__avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.tweet__content {
  flex: 1;
}

.tweet__header {
  display: flex;
  align-items: baseline;
  margin-bottom: 10px;
}

.tweet__author {
  font-weight: bold;
  font-size: 1.1rem;
  margin-right: 10px;
}

.tweet__timestamp {
  color: #64748b;
  font-size: 0.9rem;
}

.tweet__text {
  font-size: 1rem;
  line-height: 1.25;
  word-break: break-word;
}
</style>