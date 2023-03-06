<template>
    <div class="copyright">
        <div class="music-waves-2">
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
            <span></span>
        </div>
        <div class="typed-animation">
            <h1 class="typed-out">
                <p>This game made by <span>HB</span> with <span>VueJS 3</span></p>
            </h1>
        </div>
    </div>
</template>

<script>
export default {

};
</script>

<style scoped>
.copyright {
    position: fixed;
    left: 50%;
    transform: translateX(-50%);
    bottom: 0.2rem;
    color: var(--light);
    z-index: 3;
    font-size: 2rem;
    cursor: default;

}

.copyright a {
    color: #f4dc26;
}

.copyright span {
    -webkit-animation: my 5s infinite;
    -moz-animation: my 5s infinite;
    -o-animation: my 5s infinite;
    animation: my 5s infinite;
}



@-webkit-keyframes my {
    0% {
        color: darkorange;
    }

    50% {
        color: hotpink;
    }

    100% {
        color: darkturquoise;
    }
}

@-moz-keyframes my {
    0% {
        color: darkorange;
    }

    50% {
        color: hotpink;
    }

    100% {
        color: darkturquoise;
    }
}

@-o-keyframes my {
    0% {
        color: darkorange;
    }

    50% {
        color: hotpink;
    }

    100% {
        color: darkturquoise;
    }
}

@keyframes my {
    0% {
        color: darkorange;
    }

    50% {
        color: hotpink;
    }

    100% {
        color: darkturquoise;
    }
}

.music-waves-2 {
    height: 35px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.music-waves-2>span {
    display: block;
    position: relative;
    background: #000;
    height: 100%;
    width: 0.5rem;
    border-radius: 1rem;
    margin: 0 0.2rem;
    animation: waves-2 1.2s linear infinite;
}

.music-waves-2>span:nth-child(1) {
    animation-delay: 0s;
    background: #ff8c00;
}

.music-waves-2>span:nth-child(2) {
    animation-delay: 0.3s;
    background: #ffff00;
}

.music-waves-2>span:nth-child(3) {
    animation-delay: 0.6s;
    background: #26d53a;
}

.music-waves-2>span:nth-child(4) {
    animation-delay: 0.9s;
    background: #26e6a3;
}

.music-waves-2>span:nth-child(5) {
    animation-delay: 0.6s;
    background: #1da8e2;
}

.music-waves-2>span:nth-child(6) {
    animation-delay: 0.3s;
    background: #5916ba;
}

.music-waves-2>span:nth-child(7) {
    animation-delay: 0s;
    background: #d418d9;
}

@keyframes waves-2 {
    50% {
        height: 20%;
    }

    100% {
        height: 100%;
    }
}

.typed-animation {
    display: inline-block;
}

.typed-out {
    overflow: hidden;
    white-space: nowrap;
    border-right: 0.25rem solid #fff;
    font-size: 1.5rem;
    font-weight: 700;
    animation: typing 8s steps(40) infinite, blinking 1s infinite;
    margin-top: 10px;
}

@keyframes typing {

    0%,
    100% {
        width: 0;
    }

    50%,
    90% {
        width: 100%;
    }
}

@keyframes blinking {

    0%,
    100% {
        border-color: transparent;
    }

    50% {
        border-color: #fff;
    }
}
</style>