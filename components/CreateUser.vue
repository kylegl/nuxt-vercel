<script setup lang="ts">
import type { User } from '@prisma/client'

const username = $ref<string>()
let serverRouteData = $ref<User | null>()

function go() {
  const { data } = useFetch('/api/user', { body: username, method: 'POST' })
  serverRouteData = data
}
</script>

<template>
  <div>
    <input
      id="input" v-model="username" placeholder="What's your name?" type="text" autocomplete="off" p="x-4 y-2" m="t-5"
      w="250px" text="center" bg="transparent" border="~ rounded gray-200 dark:gray-700" outline="none active:none"
      @keydown.enter="go"
    >
    <div>
      <button m-3 text-sm btn :disabled="!username" @click="go">
        GO
      </button>
    </div>
    RESPONSE: {{ serverRouteData }}
  </div>
</template>
