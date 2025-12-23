<template>
    <div class="video-cutout-container">
        <video ref="bgVideo" autoplay muted playsinline loop disablepictureinpicture disableremoteplayback
            controlslist="nofullscreen noremoteplayback nodownload noplaybackrate" class="bg-video">
            <source :src="videoSrc" type="video/mp4" />
        </video>

        <div class="mask-overlay">
            <slot />
        </div>
    </div>
</template>
  
<script>
export default {
    name: "VideoCutoutHero",
    props: {
        videoSrc: { type: String, required: true },
    },
    mounted() {
        const v = this.$refs.bgVideo;
        if (v) {
            v.disablePictureInPicture = true;
            v.setAttribute("disablepictureinpicture", "");
            v.controlsList = "nofullscreen noremoteplayback nodownload";
        }
    },
};
</script>
  
<style scoped>
.video-cutout-container {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100vh;
    z-index: 1;
    overflow: hidden;
    background-color: #000;
}

.bg-video {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1.3);
    min-width: 100%;
    min-height: 100%;
    object-fit: cover;
    z-index: 1;
}

.mask-overlay {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;

    background-color: #fff;
    mix-blend-mode: screen;
    z-index: 2;
}
</style>
  