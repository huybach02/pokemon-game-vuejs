<template>
    <div class="card" :class="{ disable: isDisable }" :style="{
        height: `${(920 - 16 * 4) / Math.sqrt(cardsContext.length) - 16}px`,
        width: `${((920 - 16 * 4) / Math.sqrt(cardsContext.length) - 16 * 3 / 4)}px`
    }" v-show="isHide">
        <div class="card_inner" :class="{ 'is_flipped': isFlipped }" @click="onToggleFlipCard">
            <div class="card_face card_face-front">
                <div class="card_content" :style="{
                    backgroundSize: `${((920 - 16 * 4) / Math.sqrt(cardsContext.length) - 16 * 3 / 4) / 3}px ${((920 - 16 * 4) / Math.sqrt(cardsContext.length) - 16 * 3 / 4) / 3}px`
                }"></div>
            </div>
            <div class="card_face card_face-back">
                <div class="card_content" :style="{ backgroundImage: `url('${require('@/assets/' + imgBackFaceUrl)}')`, }">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        imgBackFaceUrl: {
            type: String,
            required: true
        },
        card: {
            type: [String, Number, Array, Object],
        },
        cardsContext: {
            type: Array,
            default: () => {
                return [];
            }
        },
        rules: {
            type: Array,
            default: () => {
                return [];
            }
        }
    },
    data() {
        return {
            isFlipped: false,
            isDisable: false,
            isHide: true
        };
    },
    methods: {
        onToggleFlipCard() {
            if (this.rules.length == 2) return;
            if (this.isDisable) return false;
            this.isFlipped = !this.isFlipped;
            if (this.isFlipped) this.$emit("onFlip", this.card);
        },
        onFlipBackCard() {
            this.isFlipped = false;
        },
        onDisableMode() {
            this.isDisable = true;
            setTimeout(() => {
                this.isHide = false;
            }, 1000);
        }
    }
};
</script>

<style scoped>
.card {
    display: inline-block;
    margin-right: 1rem;
    margin-bottom: 1rem;

}

.card.disable .card_inner {
    cursor: default;
}

.card_inner {
    width: 100%;
    height: 100%;
    transition: transform 1s;
    transform-style: preserve-3d;
    cursor: pointer;
    position: relative;
}

.card_inner.is_flipped {
    transform: rotateY(-180deg);
}

.card_face {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    overflow: hidden;
    border-radius: 1rem;
    padding: 1rem;
    box-shadow: 0 3px 10px 3px rgba(0, 0, 0, 0.2);
}

.card_face-front .card_content {
    background: url("../assets/images/icon_back.png") no-repeat center center;
    width: 100%;
    height: 100%;
}

.card_face-back {
    background-color: var(--light);
    transform: rotateY(-180deg);
}

.card_face-back .card_content {
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
    height: 100%;

}
</style>