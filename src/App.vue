<template>
    <div class="page-wrapper">
        <nav class="nav-header">
            <div class="nav-container">
                <div class="nav-logo">
                    <a href="#" class="logo-link">CryptoAlerts</a>
                </div>

                <!-- Desktop Navigation -->
                <ul class="nav-list desktop-nav">
                    <li class="nav-item"><a href="#features" @click="smoothScroll">Возможности</a></li>
                    <li class="nav-item"><a href="#fees" @click="smoothScroll">Комиссии</a></li>
                    <li class="nav-item"><a href="#partnership" @click="smoothScroll">Сотрудничество</a></li>
                    <li class="nav-item"><a href="#faq" @click="smoothScroll">FAQ</a></li>
                    <li class="nav-item"><a href="#support" @click="smoothScroll">Поддержка</a></li>
                </ul>

                <div class="nav-auth desktop-nav">
                    <a href="#login" class="auth-link">Login / Sign up</a>
                </div>

                <!-- Mobile Hamburger Button -->
                <button class="hamburger-button mobile-nav" @click="toggleMobileMenu"
                    :class="{ 'active': isMobileMenuOpen }" aria-label="Toggle navigation menu"
                    aria-expanded="isMobileMenuOpen">
                    <span class="hamburger-line"></span>
                    <span class="hamburger-line"></span>
                    <span class="hamburger-line"></span>
                </button>
            </div>
        </nav>

        <!-- Mobile Menu Overlay -->
        <transition name="mobile-menu">
            <div v-if="isMobileMenuOpen" class="mobile-menu-overlay" @click="closeMobileMenu">
                <nav class="mobile-menu-content" @click.stop>
                    <ul class="mobile-nav-list">
                        <li class="mobile-nav-item">
                            <a href="#features" @click="handleMobileNavClick">Возможности</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#fees" @click="handleMobileNavClick">Комиссии</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#partnership" @click="handleMobileNavClick">Сотрудничество</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#faq" @click="handleMobileNavClick">FAQ</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#support" @click="handleMobileNavClick">Поддержка</a>
                        </li>
                        <li class="mobile-nav-item auth-item">
                            <a href="#login" @click="closeMobileMenu" class="mobile-auth-link">
                                Login / Sign up
                            </a>
                        </li>
                    </ul>
                </nav>
            </div>
        </transition>

        <div class="video-cutout-container">
            <video ref="bgVideo" autoplay muted playsinline loop disablepictureinpicture disableremoteplayback
                controlslist="nofullscreen noremoteplayback nodownload noplaybackrate" class="bg-video">
                <source src="./assets/asd3.mp4" type="video/mp4" />
                <!-- <source src="./assets/asd3.webm" type="video/webm" /> -->
            </video>
            <div class="mask-overlay">
                <h1 class="cutout-text"
                    :class="{ 'justify-text': displayedText?.includes('CRYPTO') && displayedText?.includes('ALERTS') }"
                    :data-text="displayedText || ''">
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
                "ааа... орешки бих боб",
                "попались",
                "гнилые",
                "орешки бииих боб",
                "орешки бииих боб",
            ],
            ticking: false,
            onScrollBound: null,
            onResizeBound: null,
            isMobileMenuOpen: false,
            windowWidth: window.innerWidth, // Добавлено для отслеживания ширины окна
        };
    },
    computed: {
        // Computed property для форматирования первого текста
        formattedFirstText() {
            if (this.windowWidth < 300) {
                return "CRYPTO\nALERTS";
            }
            return "/// CRYPTO\nALERTS ///";
        }
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

        this.onResizeBound = () => {
            // Обновляем ширину окна
            this.windowWidth = window.innerWidth;

            this.updateDisplayedText();
            // Close mobile menu on resize to desktop
            if (window.innerWidth > 768 && this.isMobileMenuOpen) {
                this.closeMobileMenu();
            }
        };

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

            // Используем formattedFirstText для первого элемента
            let nextText;
            if (newTextIndex === 0) {
                nextText = this.formattedFirstText;
            } else {
                nextText = this.texts[newTextIndex];
            }

            if (nextText !== this.displayedText) {
                this.displayedText = nextText;
            }
        },

        toggleMobileMenu() {
            this.isMobileMenuOpen = !this.isMobileMenuOpen;
            // Prevent body scroll when menu is open
            if (this.isMobileMenuOpen) {
                document.body.style.overflow = 'hidden';
            } else {
                document.body.style.overflow = '';
            }
        },

        closeMobileMenu() {
            this.isMobileMenuOpen = false;
            document.body.style.overflow = '';
        },

        handleMobileNavClick(e) {
            this.smoothScroll(e);
            this.closeMobileMenu();
        },

        smoothScroll(e) {
            e.preventDefault();
            const href = e.target.getAttribute('href');
            if (href && href.startsWith('#')) {
                const element = document.querySelector(href);
                if (element) {
                    element.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            }
        },
    },
};
</script>


<style>
@import url('https://fonts.cdnfonts.com/css/sf-pro-display');

html {
    scroll-behavior: smooth;
}



.page-wrapper {
    min-height: 600vh;
}

.video-cutout-container {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100vh;
    height: 100svh;
    z-index: 1;
    overflow: hidden;
    background-color: #000;
}



.bg-video {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(.6);
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

.cutout-text {
    position: relative;
    font-size: max(10vw, 15vh);
    line-height: 100%;
    font-weight: 900;
    font-family: "Arial Black", Arial, sans-serif;
    color: #000;
    margin: 0;
    text-align: center;
    text-transform: uppercase;
    white-space: pre-line;
}

.cutout-text.justify-text {
    text-align: justify;
    text-align-last: justify;
}

.scroll-space {
    position: relative;
    z-index: 10;
    height: 100vh;
    height: 100svh;
    margin-top: 100vh;
    margin-top: 100svh;
    padding: 4rem 2rem;
    background: #1b1b1b;
    display: flex;
    align-items: center;
    justify-content: center;
}

.content-placeholder {
    text-align: center;
    font-family: "SF Pro Display", sans-serif;
    font-weight: 300;
    letter-spacing: 0.08rem;
    z-index: 20;
    color: #fff;
    max-width: 800px;
}

.content-placeholder h2 {
    font-size: 3rem;
    z-index: 20;
    margin-bottom: 1rem;
}

.content-placeholder p {
    font-size: 1.2rem;
    z-index: 20;
    line-height: 1.6;
}

.cutout-text::after {
    content: attr(data-text);
    position: absolute;
    inset: 0;
    pointer-events: none;
    color: transparent;
    text-shadow: 0 0 10px rgba(0, 0, 0, .1), 0 0 5px rgba(0, 0, 0, .5);
    mix-blend-mode: multiply;
    opacity: 1;
}

/* ========== Navigation Styles ========== */
.nav-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    background: rgba(255, 255, 255, 1);
    border-bottom: 1px solid rgba(0, 0, 0, 0.2);
    backdrop-filter: blur(10px);
    padding: 1rem 0;
}

.nav-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 0;
}

.nav-list {
    display: flex;
    align-items: center;
    justify-content: center;
    list-style: none;
    margin: 0;
    padding: 0;
    gap: 1rem;
    flex: 0;
}

.nav-item {
    flex: 0;
    text-align: center;
    padding-left: 2rem;
    padding-right: 2rem;
}

.nav-item a {
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: .5px;
    color: rgba(0, 0, 0, .9);
    text-decoration: none;
    font-family: "SF Pro Display", sans-serif;
    font-size: min(1.9vw, .875rem);
    transition: color .3s ease;
}

.nav-item a:hover {
    color: #ff6a00;
}

.nav-logo {
    padding-left: 2rem;
    flex-shrink: 0;
}

.logo-link {
    color: rgba(0, 0, 0, .9);
    text-decoration: none;
    font-family: "SF Pro Display", sans-serif;
    font-size: min(1.9vw, .875rem);
    font-weight: 600;
    transition: color .3s ease;
}

.nav-auth {
    padding-right: 2rem;
    flex-shrink: 0;
}

.auth-link {
    color: rgba(0, 0, 0, .9);
    text-decoration: none;
    font-family: "SF Pro Display", sans-serif;
    font-size: min(1.9vw, .875rem);
    font-weight: 700;
    white-space: nowrap;
    transition: color .3s ease;
}

.auth-link:hover {
    color: #ff6a00;
}

/* ========== Hamburger Button ========== */
.hamburger-button {
    display: none;
    flex-direction: column;
    justify-content: space-around;
    width: 2rem;
    height: 2rem;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    z-index: 101;
    margin-right: 1.5rem;
}

.hamburger-line {
    width: 2rem;
    height: 0.2rem;
    background: rgba(0, 0, 0, .9);
    border-radius: 10px;
    transition: all 0.3s ease;
    position: relative;
    transform-origin: 1px;
}

.hamburger-button.active .hamburger-line:nth-child(1) {
    transform: rotate(45deg);
}

.hamburger-button.active .hamburger-line:nth-child(2) {
    opacity: 0;
    transform: translateX(20px);
}

.hamburger-button.active .hamburger-line:nth-child(3) {
    transform: rotate(-45deg);
}

/* ========== Mobile Menu Overlay ========== */
.mobile-menu-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.5);
    z-index: 99;
    display: none;
}

.mobile-menu-content {
    position: absolute;
    top: 0;
    right: 0;
    width: 80%;
    max-width: 400px;
    height: 100vh;
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(20px);
    padding: 5rem 2rem 2rem;
    box-shadow: -5px 0 25px rgba(0, 0, 0, 0.1);
}

.mobile-nav-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 0;
}

.mobile-nav-item {
    border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.mobile-nav-item a {
    display: block;
    padding: 1.2rem 0;
    color: rgba(0, 0, 0, .9);
    text-decoration: none;
    font-family: "SF Pro Display", sans-serif;
    font-size: 1.1rem;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 1px;
    transition: all 0.3s ease;
}

.mobile-nav-item a:active {
    color: #ff6a00;
    transform: translateX(5px);
}

.mobile-nav-item.auth-item {
    margin-top: 2rem;
    border: none;
}

.mobile-auth-link {
    background: linear-gradient(135deg, #ff6a00 0%, #ff8c42 100%);
    color: white !important;
    padding: 1rem 2rem !important;
    border-radius: 8px;
    text-align: center;
    font-weight: 700 !important;
    box-shadow: 0 4px 15px rgba(255, 106, 0, 0.3);
}

.mobile-auth-link:active {
    transform: translateY(2px);
    box-shadow: 0 2px 8px rgba(255, 106, 0, 0.3);
}

/* ========== Mobile Menu Transitions ========== */
.mobile-menu-enter-active,
.mobile-menu-leave-active {
    transition: opacity 0.3s ease;
}

.mobile-menu-enter-active .mobile-menu-content,
.mobile-menu-leave-active .mobile-menu-content {
    transition: transform 0.3s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
    opacity: 0;
}

.mobile-menu-enter-from .mobile-menu-content {
    transform: translateX(100%);
}

.mobile-menu-leave-to .mobile-menu-content {
    transform: translateX(100%);
}

.mobile-menu-enter-to .mobile-menu-content {
    transform: translateX(0);
}

/* ========== Footer ========== */
.empty-space {
    background: transparent;
    margin-top: 0;

}

.footer {
    position: relative;
    z-index: 5;
    background: #0a0a0a;
    padding: 3rem 2rem;
    text-align: center;
    border-top: 1px solid rgba(255, 255, 255, .1);
}

.footer-content {
    max-width: 1200px;
    margin: 0 auto;
    color: rgba(255, 255, 255, .6);
    font-family: "SF Pro Display", sans-serif;
    font-size: .875rem;
}

.footer-content p {
    margin: 0;
}

/* ========== Mobile & Tablet Responsive ========== */
@media (max-width: 768px) {
    .desktop-nav {
        display: none !important;
    }

    .mobile-nav {
        display: flex !important;
    }

    .mobile-menu-overlay {
        display: block;
    }

    .nav-logo {
        padding-left: 1.5rem;
    }

    .logo-link {
        font-size: 1.1rem;
    }

    .cutout-text {
        font-size: 15vw;
    }

    .content-placeholder h2 {
        font-size: 2rem;
    }

    .content-placeholder p {
        font-size: 1rem;
    }

    .scroll-space {
        padding: 2rem 1rem;
    }
}

/* ========== Tablet Specific ========== */
@media (min-width: 769px) and (max-width: 1024px) {
    .nav-item {
        padding-left: 1rem;
        padding-right: 1rem;
    }

    .nav-item a {
        font-size: 0.8rem;
    }

    .nav-logo {
        padding-left: 1.5rem;
    }

    .nav-auth {
        padding-right: 1.5rem;
    }
}

/* ========== Small Mobile Devices ========== */
@media (min-width: 300px) and (max-width: 480px) {
    .mobile-menu-content {
        width: 85%;
    }

    .mobile-nav-item a {
        font-size: 1rem;
        padding: 1rem 0;
    }

    .logo-link {
        font-size: 1rem;
    }

    .hamburger-button {
        width: 1.75rem;
        height: 1.75rem;
        margin-right: 1rem;
    }

    .hamburger-line {
        width: 1.75rem;
    }

}


@media (max-width: 300px) {
    .cutout-text {
        position: relative;
        font-size: 15vw;
        line-height: 125%;
    }
}

/* ========== Hide Mobile Elements on Desktop ========== */
@media (min-width: 769px) {
    .mobile-nav {
        display: none !important;
    }

    .desktop-nav {
        display: flex !important;
    }
}
</style>
