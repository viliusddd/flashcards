<script setup lang="ts">
import {computed} from 'vue'
import {useDeckStore} from '@/stores/DeckStore'
import NavButtons from './NavButtons.vue'
import OptionsMenu from './OptionsMenu.vue'

const props = defineProps<{
  id: number
}>()

const deckStore = useDeckStore()

const deck = deckStore.decks.find((obj) => obj.id === props.id)

const cardsLearned = computed(
  () => deck.cards.filter((card) => card.state === 2).length
)

const progressValue = computed(() =>
  cardsLearned.value ? (cardsLearned.value / deck.cards.length) * 100 : 0
)

const difficultCardsCount = computed(
  () => deck.cards.filter((card) => card.difficulty >= 6).length
)
</script>

<template>
  <div class="wrapper">
    <div class="container">
      <div class="deck">
        <i :class="`deck__avatar pi pi-${deck.icon}`"></i>
        <div class="deck__header">
          <h1>{{ deck.name }}</h1>
          <OptionsMenu :id="deck.id" />
        </div>
        <div class="deck__stats">
          <p>
            <b>{{ progressValue.toFixed(0) }}%</b>
          </p>
          <p>
            <b>{{ cardsLearned }}/{{ deck.cards.length }}</b> items learned
          </p>
        </div>
        <ProgressBar
          class="deck__progress"
          :value="progressValue"
          :show-value="false"
        />
        <div class="deck__footer">
          <div class="deck__footer-stats">
            <div v-tooltip.bottom="'Difficult cards'">
              <i class="pi pi-bolt" />
              {{ difficultCardsCount }}
            </div>
          </div>
          <NavButtons :deck />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  --avatar-size: 4ch;
}
.container {
  border: 3px solid hsl(0, 0%, 90%);
  border-radius: 20px;
  margin: 0 0 16px 0;
  padding: 16px;
}
.deck {
  display: grid;
  align-items: center;
  gap: 0.5rem 1.5rem;
  grid-template-columns: var(--avatar-size) minmax(0px, 1fr);
  grid-template-areas:
    'avatar header'
    'stats stats'
    'progress progress'
    'footer footer';
}
.deck__avatar {
  grid-area: avatar;
  font-size: var(--avatar-size);
}
.deck__header {
  display: flex;
  grid-area: header;
  justify-content: space-between;
}
.deck__header h1 {
  margin: 4px 0 0 0;
  font-size: 2ch;
}
.deck__stats {
  display: flex;
  grid-area: stats;
  gap: 0 30px;
}
.deck__stats p {
  margin: 0;
}
.deck__progress {
  grid-area: progress;
  height: 20px;
}

.deck__footer {
  grid-area: footer;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.deck__footer-stats {
  display: flex;
  gap: 0 30px;
}
.deck__button {
  margin-left: auto;
}

@media (min-width: 30rem) {
  .deck {
    gap: 0.5rem 1.5rem;
    align-items: center;
    grid-template-columns: calc(var(--avatar-size) * 2) 1fr;
    grid-template-rows: 1fr max-content 30px 60px;
    grid-template-areas:
      'avatar header'
      'avatar stats'
      'avatar progress'
      'avatar footer';
  }
  .deck__avatar {
    font-size: calc(var(--avatar-size) * 2);
    margin-bottom: auto;
  }
  .deck__header h1 {
    font-size: 3ch;
  }
}
</style>
