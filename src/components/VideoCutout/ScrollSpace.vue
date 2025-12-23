<template>
    <div class="scroll-space">
        <slot />
    </div>
</template>
  
<script>
export default { name: "ScrollSpace" };
</script>
  
<style scoped>
.scroll-space {
    position: relative;
    z-index: 10;
    height: 100vh;
    margin-top: 100vh;
    padding: 4rem 2rem;
    background: #1b1b1b;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
  