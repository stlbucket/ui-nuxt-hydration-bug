this is a reproduction for nuxt/ui bug:

https://github.com/nuxt/ui/issues/1671

# instructions

run this app, and hit refresh until you see this warning:

```
warn [Vue warn]: Hydration attribute mismatch on 
<button class="focus:outline-none disab…nline-flex items-center" type="button" disabled=""> 
  - rendered on server: disabled="true"
  - expected on client: (not rendered)
  Note: this mismatch is check-only. The DOM will not be rectified in production due to performance overhead.
  You should fix the source of the mismatch. 
  at <Link type="button" disabled=false class="focus:outline-none disabled:cursor-not-allowed disabled:opacity-75 flex-shrink-0 font-medium rounded-md text-sm gap-x-1.5 px-2.5 py-1.5 shadow-sm text-white dark:text-gray-900 bg-primary-500 hover:bg-primary-600 disabled:bg-primary-500 dark:bg-primary-400 dark:hover:bg-primary-500 dark:disabled:bg-primary-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-primary-500 dark:focus-visible:outline-primary-400 inline-flex items-center"  ... > 
  at <Button disabled=false onClick=fn<onClicked> > 
  at <App key=3 > 
  at <NuxtRoot>
```

this happens when disabled can change

if you take away the `disabled` property, there is no error

```
// app.vue

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
```


