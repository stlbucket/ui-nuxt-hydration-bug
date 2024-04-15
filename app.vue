<template>
  <div class="flex justify-around">
    <UButton 
      @click="onClicked"
      :disabled="disableButton"
    >This is a button with the warning - comment it out to remove warning
    </UButton>
    <UButton 
      @click="onClicked"
    >This is a button with no warning
    </UButton>
  </div>
</template>

<script setup lang="ts">
  const disableButton = computed(() => Math.random() > .5)

  const onClicked = () => {
    alert('clicked')
  }
</script>
