<script setup lang="ts">
import { onMounted, ref } from "vue";

// import { Icon } from "@iconify/vue";
const isRendered = ref(false);

onMounted(() => {
  setTimeout(() => {
    isRendered.value = true;
  }, 500);
});
</script>

<template>
  <main id="mainContainer" class="min-h-screen">
    <!-- <button class="p-4" @click="isRendered = !isRendered">Click!</button> -->

    <Transition name="slide">
      <div v-if="isRendered" class="card">
        <form action="">
          <h1 class="card__title">Enter Payment Information</h1>
          <div class="card__row">
            <div class="card__col">
              <label for="cardNumber" class="card__label">Card Number</label>
              <input
                type="text"
                class="card__input card__input--large"
                id="cardNumber"
                placeholder="xxxx-xxxx-xxxx-xxxx" />
            </div>
            <div class="card_-col card__chip">
              <img src="../assets/chip.svg" alt="chip" />
            </div>
          </div>

          <div class="card__row">
            <div class="card_-col">
              <label for="cardExpiry" class="card__label">Expire Date</label>
              <input id="cardExpiry" type="text" class="card__input" placeholder="xx/xx" />
            </div>
            <div class="card_-col">
              <label for="cardCcv" class="card__label">CCV</label>
              <input id="cardCcv" type="text" class="card__input" placeholder="xxx" />
            </div>
            <div class="card__col card__brand">
              <i id="CardBrand"></i>
            </div>
          </div>
        </form>
      </div>
    </Transition>
  </main>
</template>

<style>
@reference "@/style.css";

#mainContainer {
  @apply flex items-center justify-center bg-purple-700 bg-[url('@/assets/bg.svg')] bg-center bg-cover overflow-hidden;
}
.card {
  @apply bg-linear-to-br from-white/20 to-white/5 shadow-2xl backdrop-blur-sm p-6 rounded-xl;
}
.card__row {
  @apply flex justify-between pb-8;
}
.card__title {
  @apply text-4xl font-semibold text-[#1d005f] mt-4 mx-0 mb-6;
  text-shadow: 0 2px 2px rgba(0, 0, 0, 0.3);
}
.card__col {
  @apply pr-8;
}
.card__input {
  @apply border-b border-dashed border-white/40 text-white focus:outline-none focus:border-white/80;
}
.card__input--large {
  @apply text-4xl;
}
.card__label {
  @apply block text-white font-normal;
}
.card__chip {
  @apply self-end;
}
.card__chip img {
  @apply w-12;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.5s ease-in-out;
}
.slide-enter-from {
  opacity: 0;
  transform: translateX(-20px);
}
.slide-leave-to {
  opacity: 0;
  transform: translateX(20px);
}
</style>
