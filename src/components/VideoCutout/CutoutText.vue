<template>
    <h1 class="cutout-text" :data-text="text">{{ text }}</h1>
</template>
  
<script>
export default {
    name: "CutoutText",
    props: {
        text: { type: String, required: true },
    },
};
</script>
  
<style scoped>
.cutout-text {
    position: relative;
    font-size: 10vw;
    font-weight: 900;
    font-family: sans-serif;
    color: #000;
    margin: 0;
    text-align: center;
    text-transform: uppercase;
}

.cutout-text::after {
    content: attr(data-text);
    position: absolute;
    inset: 0;
    pointer-events: none;
    color: transparent;
    text-shadow:
        0 0 10px rgba(0, 0, 0, 0.3),
        0 0 5px rgba(0, 0, 0, 1);
    mix-blend-mode: multiply;
    opacity: 1;
}
</style>
  