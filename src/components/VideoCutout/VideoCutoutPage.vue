<template>
    <div class="page-wrapper">
        <VideoCutoutHero :video-src="videoUrl">
            <CutoutText :text="displayedText" />
        </VideoCutoutHero>

        <ScrollSpace ref="scrollSpace">
            <div class="content-placeholder">
                <h2>Контент ниже</h2>
                <p>Здесь может быть любой контент...</p>
            </div>
        </ScrollSpace>
    </div>
</template>
  
<script>
import videoUrl from "@/assets/asd3.mp4";
import VideoCutoutHero from "./VideoCutoutHero.vue";
import CutoutText from "./CutoutText.vue";
import ScrollSpace from "./ScrollSpace.vue";

export default {
    name: "VideoCutoutPage",
    components: { VideoCutoutHero, CutoutText, ScrollSpace },
    data() {
        return {
            videoUrl,
            displayedText: "CRYPTO ALERTS",
            ticking: false,
            onScrollBound: null,
            onResizeBound: null,
            onKeydownBound: null,
            onWheelBound: null,
            onGestureBound: null,
        };
    },
    mounted() {
        this.onScrollBound = () => {
            if (this.ticking) return;
            this.ticking = true;
            window.requestAnimationFrame(() => {
                this.updateDisplayedText();
                this.ticking = false;
            });
        };

        this.onResizeBound = () => this.updateDisplayedText();

        window.addEventListener("scroll", this.onScrollBound, { passive: true });
        window.addEventListener("resize", this.onResizeBound);

        this.onWheelBound = (e) => {
            if (e.ctrlKey || e.metaKey) e.preventDefault();
        };
        this.onKeydownBound = (e) => {
            if ((e.ctrlKey || e.metaKey) && ["+", "-", "=", "0"].includes(e.key)) e.preventDefault();
        };
        this.onGestureBound = (e) => e.preventDefault();

        window.addEventListener("wheel", this.onWheelBound, { passive: false });
        window.addEventListener("keydown", this.onKeydownBound);
        window.addEventListener("gesturestart", this.onGestureBound);
        window.addEventListener("gesturechange", this.onGestureBound);
        window.addEventListener("gestureend", this.onGestureBound);

        this.updateDisplayedText();
    },
    beforeDestroy() { this.cleanup(); },
    beforeUnmount() { this.cleanup(); },
    methods: {
        cleanup() {
            if (this.onScrollBound) window.removeEventListener("scroll", this.onScrollBound);
            if (this.onResizeBound) window.removeEventListener("resize", this.onResizeBound);
            if (this.onWheelBound) window.removeEventListener("wheel", this.onWheelBound);
            if (this.onKeydownBound) window.removeEventListener("keydown", this.onKeydownBound);
            if (this.onGestureBound) {
                window.removeEventListener("gesturestart", this.onGestureBound);
                window.removeEventListener("gesturechange", this.onGestureBound);
                window.removeEventListener("gestureend", this.onGestureBound);
            }
        },

        updateDisplayedText() {
            const comp = this.$refs.scrollSpace;
            const panelEl = comp && comp.$el ? comp.$el : null; // root DOM элемента дочернего компонента
            if (!panelEl) return;

            const rect = panelEl.getBoundingClientRect();
            const swapLine = window.innerHeight * 0.5 - 700;
            const shouldBeAnother = rect.top <= swapLine;

            const nextText = shouldBeAnother ? "SAFE. FAST. CRYPTO." : "///CRYPTO ALERTS///";
            if (nextText !== this.displayedText) this.displayedText = nextText;
        },
    },
};
</script>
  
<style scoped>
.page-wrapper {
    min-height: 200vh;
}

.content-placeholder {
    text-align: center;
    color: white;
    max-width: 800px;
}

.content-placeholder h2 {
    font-size: 3rem;
    margin-bottom: 1rem;
}

.content-placeholder p {
    font-size: 1.2rem;
    line-height: 1.6;
}
</style>
  