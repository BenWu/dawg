<script setup lang="ts">

import { ref, provide, shallowRef } from 'vue';

import { sources } from './config';
import type { DAWGMap, DAWGSet } from '@/workgroups';

import DataLoader from '@/components/DataLoader.vue'
import HeaderNav from '@/components/HeaderNav.vue'
import { datamapinjection, datasetinjection } from '@/injections';

const hasLoaded = ref(false)

const datamap = shallowRef(new Map() as DAWGMap)
const dataset = shallowRef([] as DAWGSet)

provide(datamapinjection, datamap)
provide(datasetinjection, dataset)

const recieveData = (recievedMap: DAWGMap, recievedSet: DAWGSet) => {
  console.log('recieved data')
  datamap.value = recievedMap
  dataset.value = recievedSet
  hasLoaded.value = true
}

</script>

<template>
  <HeaderNav />
  <main>
    <DataLoader v-if="!hasLoaded" :sources="sources" @done="recieveData" />
    <RouterView v-else />
  </main>
</template>

<style>
header {
  margin: 1rem auto 2rem;
}

.monospace {
  font-family: monospace;
}

.container {
  width: 100%;
  margin: 0px auto;
}
</style>
