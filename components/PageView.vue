<script setup lang="ts">
const { data } = await useFetch('/api/pageview')
const { width: windowWidth } = useWindowSize({ initialHeight: 0, initialWidth: 0 })

const time = useTimeAgo(computed(() => data.value.startAt))
</script>

<template>
  <div :class="{ 'text-red-500': windowWidth < 1200 }">
    <span font-500 text-gray>{{ data.pageview }}</span>
    page views since
    <span text-gray>{{ time }}</span>

    <br />
    <br />

    <p>windowWidth: {{ windowWidth }}</p>
    <p>
      Red color is applied if width is
      <code>&lt; 1200</code>
    </p>
    <p>
      If you reload the page in
      <code>> 1200</code>, text still get
      <code>disabled</code> class
    </p>

    <br />
    <br />

    <p
      text-blue-500
    >Expected result: {{ windowWidth < 1200 ? 'color should be red' : 'color should not be red' }}</p>
    <p text-yellow-500>Note: Reload the page and try</p>
  </div>
</template>
