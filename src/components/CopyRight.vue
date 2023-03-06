<template>
    <div class="copyright">
        <p>This game made by <span>HB</span> with <span>VueJS 3</span></p>
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
    bottom: 1.5rem;
    color: var(--light);
    z-index: 3;
    font-size: 1.5rem;
}

.copyright a {
    color: #f4dc26;
}

.copyright span {
    color: cyan;
}
</style>