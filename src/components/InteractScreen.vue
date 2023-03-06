<template>
    <div class="screen">
        <div class="screen_inner" :style="{
            width: `${((((920 - 16 * 4) / Math.sqrt(cardsContext.length) - 16 * 3 / 4) + 16) * Math.sqrt(cardsContext.length))}px`
        }">
            <CardFlip v-for="(card, index) in cardsContext" :key="index" :imgBackFaceUrl="`images/${card}.png`"
                :card="{ index: index, value: card }" @onFlip="checkRule($event)" :ref="`card-${index}`"
                :cardsContext="cardsContext" :rules="rules" />
        </div>
    </div>
</template>

<script>
import CardFlip from "./Card_Item.vue";

export default {
    props: {
        cardsContext: {
            type: Array,
            default: () => {
                return [];
            }
        }
    },
    components: {
        CardFlip
    },
    data() {
        return {
            rules: []
        };
    },
    methods: {
        checkRule(card) {
            if (this.rules.length === 2) return false;
            this.rules.push(card);
            if (this.rules[0].index != this.rules[1].index) {
                if (this.rules.length === 2 && this.rules[0].value === this.rules[1].value) {
                    console.log("right");
                    this.$refs[`card-${this.rules[0].index}`][0].onDisableMode();
                    this.$refs[`card-${this.rules[1].index}`][0].onDisableMode();
                    this.rules = [];

                    const disabledElements = document.querySelectorAll(".screen .card.disable");
                    if (disabledElements && disabledElements.length === this.cardsContext.length - 2) {
                        setTimeout(() => {
                            this.$emit("onFinish");
                        }, 1000);
                    }


                }
                else if (this.rules.length === 2 && this.rules[0].value !== this.rules[1].value) {
                    console.log("Wrong");

                    setTimeout(() => {
                        this.$refs[`card-${this.rules[0].index}`][0].onFlipBackCard();
                        this.$refs[`card-${this.rules[1].index}`][0].onFlipBackCard();
                        this.rules = [];
                    }, 1000);


                }
                else return false;
            }
            else {
                this.rules = [];
            }
        }
    }
};
</script>

<style>
.screen {
    width: 100%;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
    background-color: var(--dark);
    color: var(--light)
}

.screen_inner {
    display: flex;
    flex-wrap: wrap;
    margin: 2rem auto;
}
</style>