<template>
    <div class="page-wrapper">
        <nav class="nav-header">
            <div class="nav-container">
                <div class="nav-logo">
                    <a href="#" class="logo-link">CryptoAlerts</a>
                </div>
                <ul class="nav-list">
                    <li class="nav-item"><a href="#features">Возможности</a></li>
                    <li class="nav-item"><a href="#fees">Комиссии</a></li>
                    <li class="nav-item"><a href="#partnership">Сотрудничество</a></li>
                    <li class="nav-item"><a href="#faq">FAQ</a></li>
                    <li class="nav-item"><a href="#support">Поддержка</a></li>
                </ul>
                <div class="nav-auth">
                    <a href="#login" class="auth-link">Login / Sign up</a>
                </div>
            </div>
        </nav>
        <div class="video-cutout-container">
            <video ref="bgVideo" autoplay muted playsinline loop disablepictureinpicture disableremoteplayback
                controlslist="nofullscreen noremoteplayback nodownload noplaybackrate" class="bg-video">
                <source src="./assets/asd3.mp4" type="video/mp4" />
            </video>
            <div class="mask-overlay">
                <h1 class="cutout-text"
                    :class="{ 'justify-text': displayedText.includes('CRYPTO') && displayedText.includes('ALERTS') }"
                    :data-text="displayedText">
                    {{ displayedText }}
                </h1>
            </div>
        </div>
        <div id="features" class="scroll-space" ref="section1">
            <div class="content-placeholder">
                <h2>Возможности</h2>
                <p>Мощные инструменты для работы с криптовалютой...</p>
            </div>
        </div>
        <div id="fees" class="scroll-space" ref="section2">
            <div class="content-placeholder">
                <h2>Комиссии</h2>
                <p>Прозрачные и минимальные комиссии...</p>
            </div>
        </div>
        <div id="partnership" class="scroll-space" ref="section3">
            <div class="content-placeholder">
                <h2>Сотрудничество</h2>
                <p>Партнерская программа для креаторов...</p>
            </div>
        </div>
        <div id="faq" class="scroll-space" ref="section4">
            <div class="content-placeholder">
                <h2>FAQ</h2>
                <p>Ответы на часто задаваемые вопросы...</p>
            </div>
        </div>
        <div id="support" class="scroll-space" ref="section5">
            <div class="content-placeholder">
                <h2>Поддержка</h2>
                <p>Круглосуточная поддержка пользователей...</p>
            </div>
        </div>
        <div class="scroll-space empty-space" ref="section6">
        </div>
        <footer class="footer">
            <div class="footer-content">
                <p>&copy; 2025 Crypto Alerts. All rights reserved.</p>
            </div>
        </footer>
    </div>
</template>

<script>
export default {
    name: "VideoCutout",
    data() {
        return {
            displayedText: "/// CRYPTO\nALERTS ///",
            texts: [
                "/// CRYPTO\nALERTS ///",
                "SAFE. FAST. CRYPTO.",
                "БИХ БОБ ОРЕШКИ",
                "попались",
                "гнилые",
                "орешки бих боб"
            ],
            ticking: false,
            onScrollBound: null,
            onResizeBound: null,
        };
    },
    mounted() {
        const video = this.$refs.bgVideo;
        if (video) {
            video.playbackRate = 0.8;
        }
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

        this.updateDisplayedText();

        const v = this.$refs.bgVideo;
        if (v) {
            v.disablePictureInPicture = true;
            v.setAttribute("disablepictureinpicture", "");
            v.controlsList = "nofullscreen noremoteplayback nodownload";
        }
    },
    beforeDestroy() {
        this.cleanup();
    },
    beforeUnmount() {
        this.cleanup();
    },
    methods: {
        cleanup() {
            if (this.onScrollBound) window.removeEventListener("scroll", this.onScrollBound);
            if (this.onResizeBound) window.removeEventListener("resize", this.onResizeBound);
        },

        updateDisplayedText() {
            const sections = [
                this.$refs.section1,
                this.$refs.section2,
                this.$refs.section3,
                this.$refs.section4,
                this.$refs.section5,
                this.$refs.section6,
            ];

            const centerLine = window.innerHeight * 0.3;
            let newTextIndex = 0;

            for (let i = 0; i < sections.length; i++) {
                const section = sections[i];
                if (!section) continue;

                const rect = section.getBoundingClientRect();
                if (rect.top <= centerLine) {
                    newTextIndex = i + 1;
                }
            }

            const nextText = this.texts[newTextIndex];
            if (nextText !== this.displayedText) {
                this.displayedText = nextText;
            }
        },
    },
};
</script>


<style>
@import url('https://fonts.cdnfonts.com/css/sf-pro-display');

html {
    scroll-behavior: smooth
}

.page-wrapper {
    min-height: 600vh
}

.video-cutout-container {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100vh;
    z-index: 1;
    overflow: hidden;
    background-color: #000
}

.bg-video {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(.6);
    min-width: 100%;
    min-height: 100%;
    object-fit: cover;
    z-index: 1
}

.mask-overlay {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #fff;
    mix-blend-mode: screen;
    z-index: 2
}

.cutout-text {
    position: relative;
    font-size: max(10vw, 15vh);
    line-height: 100%;
    font-weight: 900;
    font-family: sans-serif;
    color: #000;
    margin: 0;
    text-align: center;
    text-transform: uppercase;
    white-space: pre-line
}

.cutout-text.justify-text {
    text-align: justify;
    text-align-last: justify
}

.scroll-space {
    position: relative;
    z-index: 10;
    height: 100vh;
    margin-top: 100vh;
    padding: 4rem 2rem;
    background: #1b1b1b;
    display: flex;
    align-items: center;
    justify-content: center
}

.content-placeholder {
    text-align: center;
    z-index: 20;
    color: #fff;
    max-width: 800px
}

.content-placeholder h2 {
    font-size: 3rem;
    z-index: 20;
    margin-bottom: 1rem
}

.content-placeholder p {
    font-size: 1.2rem;
    z-index: 20;
    line-height: 1.6
}

.cutout-text::after {
    content: attr(data-text);
    position: absolute;
    inset: 0;
    pointer-events: none;
    color: transparent;
    text-shadow: 0 0 10px rgba(0, 0, 0, .1), 0 0 5px rgba(0, 0, 0, .5);
    mix-blend-mode: multiply;
    opacity: 1
}

.nav-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    background: rgba(255, 255, 255, .8);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid #000;
    padding: 1rem 0
}

.nav-container,
.nav-list {
    display: flex;
    align-items: center;
    padding: 0
}

.nav-container {
    justify-content: space-between;
    width: 100%
}

.nav-list {
    justify-content: center;
    list-style: none;
    margin: 0;
    gap: 1rem;
    flex: 0
}

.nav-item {
    flex: 0;
    text-align: center;
    padding-left: 2rem;
    padding-right: 2rem
}

.nav-item a {
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: .5px
}

.auth-link:hover,
.nav-item a:hover {
    color: #ff6a00
}

.nav-logo {
    padding-left: 2rem;
    flex-shrink: 0
}

.logo-link,
.nav-item a {
    color: rgba(0, 0, 0, .9);
    text-decoration: none;
    font-family: "SF Pro Display", sans-serif;
    font-size: min(1.9vw, .875rem);
    transition: color .3s ease
}

.logo-link {
    font-weight: 600
}

.nav-auth {
    padding-right: 2rem;
    flex-shrink: 0
}

.auth-link {
    color: rgba(0, 0, 0, .9);
    text-decoration: none;
    font-family: "SF Pro Display", sans-serif;
    font-size: min(1.9vw, .875rem);
    font-weight: 700;
    white-space: nowrap;
    transition: color .3s ease
}

.empty-space {
    background: 0 0;
    margin-top: 0
}

.footer {
    position: relative;
    z-index: 10;
    background: #0a0a0a;
    padding: 3rem 2rem;
    text-align: center;
    border-top: 1px solid rgba(255, 255, 255, .1)
}

.footer-content {
    max-width: 1200px;
    margin: 0 auto;
    color: rgba(255, 255, 255, .6);
    font-family: "SF Pro Display", sans-serif;
    font-size: .875rem
}

.footer-content p {
    margin: 0
}

@media (max-width:740px) {
    .cutout-text {
        font-size: 15vw
    }

    .nav-container {
        flex-direction: column;
        gap: 1rem
    }

    .nav-list {
        gap: 1rem;
        flex-wrap: wrap
    }
}
</style>
