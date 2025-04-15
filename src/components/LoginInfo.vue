<script setup>
import IconSparkles from './icons/IconSparkles.vue'
</script>

<template>
  <section class="login-info">
    <div class="login-info__icon">
      <IconSparkles />
    </div>
    <div class="login-info__content">
      <h2 class="login-info__heading">
        Du bist nicht angemeldet
      </h2>
      <div class="login-info__action">
        <a href="#" class="btn btn--transparent">
          Zum Login &nbsp; &rarr;
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.login-info {
  padding: 20px;
  color: #f1f5f9;
  background: #334155;
  position: sticky;
  top: 0;
  z-index: 10;
}

.login-info__icon svg {
  width: 50px;
}

.login-info__heading {
  margin: 0;
  line-height: 1;
  font-size: 1.2rem;
  font-weight: bold;
  margin: 20px 0;
}

.login-info__content {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
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
  transition: background .2s ease-out;
  white-space: nowrap;
  justify-content: center;
  cursor: pointer;
}

.btn--transparent {
  background: rgba(255, 255, 255, .2);
  color: #fff;
}

.btn[disabled] {
  opacity: 0.5;
  pointer-events: none;
}
</style>