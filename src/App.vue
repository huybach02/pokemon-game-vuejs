<template>
  <div>
    <MainScreen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)" />
    <InteractScreen v-if="statusMatch === 'match'" :cardsContext="setting.cardsContext" @onFinish="onGetResult" />
    <ResultScreen v-if="statusMatch === 'result'" :timer="timer" @onStartAgain="statusMatch = 'default'" />
    <CopyRight />
  </div>
</template>

<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from "./components/InteractScreen.vue";
import ResultScreen from "./components/ResultScreen.vue";
import CopyRight from "./components/CopyRight.vue";

import { shuffled } from "../utils/array";

export default {
  name: 'App',
  data() {
    return {
      statusMatch: "default",
      setting: {
        totalOfBlock: 0,
        cardsContext: [],
        startedAt: null,
      },
      timer: 0
    };
  },
  components: {
    MainScreen,
    InteractScreen,
    ResultScreen,
    CopyRight,
  },
  methods: {
    onHandleBeforeStart(config) {
      this.setting.totalOfBlock = config.totalOfBlock;
      const firstCards = Array.from({ length: this.setting.totalOfBlock / 2 }, (_, i) => i + 1);
      const secondCards = [...firstCards];
      const cards = [...firstCards, ...secondCards];
      this.setting.cardsContext = shuffled(shuffled(shuffled(cards)));

      this.setting.startedAt = new Date().getTime();

      this.statusMatch = "match";
    },
    onGetResult() {
      this.timer = new Date().getTime() - this.setting.startedAt;

      this.statusMatch = "result";
    }
  }
};
</script>

<style></style>
