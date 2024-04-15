<template>
  <div>
    <UButton 
      :disabled="disableButton"
      @click="onClicked"
    >This is a button</UButton>
  </div>
</template>

<script setup lang="ts">
  const disableButton = computed(() => Math.random() > .5)

  const onClicked = () => {
    alert('clicked')
  }
</script>
