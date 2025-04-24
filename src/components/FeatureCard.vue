<template>
  <div v-if="feature" class="info-card">
    <h3>Feature Info</h3>
    <p><strong>ID:</strong> {{ feature.id }}</p>
    <p><strong>Type:</strong> {{ feature.type }}</p>
  </div>
</template>

<script>
export default {
  name: 'FeatureCard',
  props: {
    feature: Object
  }
}
</script>

<style scoped>
.info-card {
  margin-top: 1rem;
  padding: 1rem;
  background-color: #f4f4f4;
  border-radius: 10px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.1);
}
</style>
