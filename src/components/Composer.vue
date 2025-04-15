<script setup>
import { ref, computed } from 'vue'
import { createTweet } from '../api/requests'

const emit = defineEmits(['posted'])
const tweetText = ref('')
const tweetLength = computed(() => tweetText.value.length)
const isButtonDisabled = computed(() => tweetLength.value < 5)

async function handleSubmit() {
  await createTweet(tweetText.value)
  emit('posted') 
  tweetText.value = '' 
}
</script>

<template>
  <form class="composer" @submit.prevent="handleSubmit">
    <label class="composer__prompt">Was geht?</label>
    <textarea
        v-model="tweetText"
        maxlength="160"
        class="composer__textarea"
        placeholder="Verfasse einen Tweet..."
    />
    <div class="composer__actions">
      <div class="composer__stats stats">
        <span class="stats__counter">{{ tweetLength }}</span>
        <span class="stats__max">/ 160</span>
      </div>
      <button :disabled="isButtonDisabled" class="btn btn--primary">
        Tweet veröffentlichen
      </button>
    </div>
  </form>
</template>

<style scoped>
.composer {
  position: relative;
  display: block;
}

.composer__prompt {
  color: #64748b;
  padding: 20px 20px 0;
  font-weight: bold;
  font-size: 1.1rem;
  display: block;
}

.composer__textarea {
  color: inherit;
  font-family: inherit;
  font-size: 1.4rem;
  background: transparent;
  padding: 5px 20px 0;
  width: 100%;
  height: 140px;
  margin-top: 5px;
  border: none;
  resize: none;
}

.composer__textarea:focus {
  outline: none;
}

.composer__textarea::placeholder {
  color: #475569;
}

.composer__actions {
  border-bottom: 1px solid #1e293b;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.stats {
  display: flex;
  align-items: center;
}

.stats__counter {
  font-size: 1.2rem;
  font-weight: bold;
  margin-right: 5px;
}

.stats__max {
  font-size: 1.1rem;
  color: #64748b;
  padding-left: 2px;
}

.btn {
  line-height: 1;
  font-weight: bold;
  height: 40px;
  border-radius: 20px;
  border: none;
  appearance: none;
  padding: 4px 20px;
  background: #64748b;
  color: #e2e8f0;
  display: inline-flex;
  align-items: center;
  transition: background 0.2s ease-out;
  white-space: nowrap;
  justify-content: center;
  cursor: pointer;
}

.btn--primary {
  background: #e11d48;
  color: #fff;
}

.btn--primary:hover {
  background: #f43f5e;
}

.btn[disabled] {
  opacity: 0.5;
  pointer-events: none;
}
</style>