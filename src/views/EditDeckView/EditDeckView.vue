<script setup lang="ts" generic="T">
import {computed} from 'vue'
import {useDeckStore} from '@/stores/DeckStore'
import {useTitle} from '@vueuse/core'
import CardDialog from './CardDialog.vue'
import CardsTable from './CardsTable.vue'
import DeleteCardDialog from './DeleteCardDialog.vue'
import DeleteCardsDialog from './DeleteCardsDialog.vue'
import HoverButton from './HoverButton.vue'
import ToolBar from './ToolBar.vue'

const deckStore = useDeckStore()

const props = defineProps<{
  id: number
}>()

deckStore.deckId = props.id

const title = computed(() => `Edit: ${deckStore.deck.name}`)
useTitle(title)
</script>

<template>
  <div>
    <HoverButton :id size="2.5ch" :isBold="true" attribute="name" />
    <HoverButton :id size="2ch" :isBold="false" attribute="description" />
    <ToolBar />
    <CardsTable />
    <CardDialog />
    <DeleteCardDialog />
    <DeleteCardsDialog />
  </div>
</template>

<style scoped>
header {
  margin: 0 0 20px 0;
}
</style>
