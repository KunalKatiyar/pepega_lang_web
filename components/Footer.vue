<script setup lang="ts">
const links = [{
  label: 'Other Projects',
  children: [{
    label: 'Mediavibe',
    to: 'https://github.com/KunalKatiyar/mediavibe',
    target: '_self'
  }, {
    label: 'Santulankarta',
    to: 'https://github.com/KunalKatiyar/santulankarta',
    target: '_self'
  }, {
    label: 'ChatBox',
    to: 'https://github.com/KunalKatiyar/ChatBox-App',
    target: '_self'
  }]
}, {
  label: 'Links',
  children: [{
    label: 'Rust',
    to: 'https://www.rust-lang.org/',
    target: '_self'
  }, {
    label: 'Twitch',
    to: 'https://twitch.tv',
    target: '_self'
  }, {
    label: 'Crafting Interpreters',
    to: 'https://www.rust-lang.org/',
    target: '_self'
  }]
}, {
  label: 'Social Media',
  children: [{
    label: 'Github',
    to: 'https://github.com/KunalKatiyar',
    target: '_self'
  }, {
    label: 'Twitter',
    to: 'https://twitter.com/OneEyedGhost20',
    target: '_self'
  }, {
    label: 'Portfolio',
    to: 'https://kunalkatiyar.vercel.app/',
    target: '_self'
  }]
}]

const toast = useToast()

const email = ref('')
const loading = ref(false)

function onSubmit () {
  loading.value = true

  setTimeout(() => {
    toast.add({
      title: 'Subscribed!',
      description: 'You\'ve been subscribed to our newsletter.'
    })

    loading.value = false
  }, 1000)
  console.log("Submitted!");
}
</script>

<template>
  <UFooter>
    <template #top>
      <UFooterColumns :links="links" >
        <template #right>
          <form @submit.prevent="onSubmit">
            <UFormGroup label="Subscribe to our newsletter" :ui="{ container: 'mt-3' }">
              <UInput v-model="email" type="email" placeholder="Enter your email" :ui="{ icon: { trailing: { pointer: '' } } }" required size="xl" autocomplete="off" class="max-w-sm">
                <template #trailing>
                  <UButton type="submit" size="xs" :label="loading ? 'Subscribing' : 'Subscribe'" :loading="loading" />
                </template>
              </UInput>
            </UFormGroup>
          </form>
        </template>
      </UFooterColumns>
    </template>

    <template #left>
      <p class="text-gray-500 dark:text-gray-400 text-sm">
        Copyright © {{ new Date().getFullYear() }}. All rights reserved.
      </p>
    </template>

    <template #right>
      <UColorModeButton size="sm" />

      <UButton to="https://github.com/KunalKatiyar" target="_blank" icon="i-simple-icons-github" aria-label="GitHub" color="gray" variant="ghost" />
    </template>
  </UFooter>
</template>
