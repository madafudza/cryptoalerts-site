<template>
    <div class="page-wrapper">
        <!-- Navigation остается без изменений -->
        <nav class="nav-header">
            <div class="nav-container">
                <div class="nav-logo">
                    <a href="#" class="logo-link">CryptoAlerts</a>
                </div>

                <ul class="nav-list desktop-nav">
                    <li class="nav-item"><a href="#features" @click="smoothScroll">Features</a></li>
                    <li class="nav-item"><a href="#fees" @click="smoothScroll">Fees</a></li>
                    <li class="nav-item"><a href="#partnership" @click="smoothScroll">Partnership</a></li>
                    <li class="nav-item"><a href="#faq" @click="smoothScroll">FAQ</a></li>
                    <li class="nav-item"><a href="#support" @click="smoothScroll">Support</a></li>
                </ul>

                <div class="nav-auth desktop-nav">
                    <a href="#login" class="auth-link">Login / Sign up</a>
                </div>

                <button class="hamburger-button mobile-nav" @click="toggleMobileMenu"
                    :class="{ 'active': isMobileMenuOpen }">
                    <span class="hamburger-line"></span>
                    <span class="hamburger-line"></span>
                    <span class="hamburger-line"></span>
                </button>
            </div>
        </nav>

        <!-- Mobile Menu -->
        <transition name="mobile-menu">
            <div v-if="isMobileMenuOpen" class="mobile-menu-overlay" @click="closeMobileMenu">
                <nav class="mobile-menu-content" @click.stop>
                    <ul class="mobile-nav-list">
                        <li class="mobile-nav-item">
                            <a href="#features" @click="handleMobileNavClick">Features</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#fees" @click="handleMobileNavClick">Fees</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#partnership" @click="handleMobileNavClick">Partnership</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#faq" @click="handleMobileNavClick">FAQ</a>
                        </li>
                        <li class="mobile-nav-item">
                            <a href="#support" @click="handleMobileNavClick">Support</a>
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

        <!-- Video Background -->
        <div class="video-cutout-container">
            <video ref="bgVideo" autoplay muted playsinline loop disablepictureinpicture class="bg-video">
                <source src="./assets/asd3.mp4" type="video/mp4" />
            </video>
            <div class="mask-overlay">
                <h1 class="cutout-text"
                    :class="{ 'justify-text': displayedText?.includes('CRYPTO') && displayedText?.includes('ALERTS') }"
                    :data-text="displayedText || ''">
                    {{ displayedText }}
                </h1>
            </div>
        </div>

        <!-- FEATURES SECTION -->
        <div id="features" class="scroll-space" ref="section1">
            <div class="content-section features-content">
                <div class="section-header">
                    <span class="section-number">01</span>
                    <h2>What we do</h2>
                </div>

                <p class="section-description">
                    CryptoAlerts is a platform for accepting donations in cryptocurrency.
                    It provides streamers and content creators with instant USDT donations
                    on TRON network, real-time alerts, custom donation pages, and secure
                    wallet management. No middlemen, no delays - just pure crypto support
                    from your community.
                </p>

                <div class="feature-grid">
                    <div class="feature-item">
                        <h3>Instant Crypto Donations</h3>
                        <p>Accept USDT directly on TRON network. No middlemen, no BS. Just straight crypto from your fans to
                            your wallet.</p>
                    </div>

                    <div class="feature-item highlight">
                        <h3>Real-time Alerts</h3>
                        <p>Get notified instantly when someone drops you crypto. Perfect for streamers who want that live
                            engagement with their community.</p>
                    </div>

                    <div class="feature-item">
                        <h3>Custom Donation Pages</h3>
                        <p>Your link, your style. Create a personalized donation page that actually looks good and works
                            seamlessly.</p>
                    </div>

                    <div class="feature-item">
                        <h3>OBS Integration</h3>
                        <p>Plug into your stream with our widget. Show off those donations in real-time. Your viewers will
                            love it.</p>
                    </div>

                    <div class="feature-item highlight">
                        <h3>Secure & Private</h3>
                        <p>We use HD wallets with child addresses for every transaction. Your funds stay yours, always.</p>
                    </div>

                    <div class="feature-item">
                        <h3>Dashboard That Makes Sense</h3>
                        <p>Track your earnings, manage withdrawals, check history. Everything in one place without the
                            clutter.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="floating-text-wrapper">
            <p class="floating-text">Soo.. it's just</p>
        </div>

        <!-- FEES SECTION -->
        <div id="fees" class="scroll-space" ref="section2">
            <div class="content-section fees-content">
                <div class="section-header">
                    <span class="section-number">02</span>
                    <h2>Pricing</h2>
                </div>

                <div class="fees-layout">
                    <div class="fee-visual">
                        <!-- <div class="big-seven">7<span class="percent">%</span></div> -->
                        <div class="big-seven"><img src="./assets/7.png" alt="7%"></div>
                    </div>

                    <div class="fee-details">
                        <h3>That's it. Just 7%.</h3>
                        <p>No hidden fees, no monthly subscriptions, no surprise charges. We take 7% from each donation, and
                            that's literally it.</p>

                        <div class="fee-breakdown">
                            <div class="breakdown-item">
                                <span class="label">Platform fee:</span>
                                <span class="value">7%</span>
                            </div>
                            <div class="breakdown-item">
                                <span class="label">Setup cost:</span>
                                <span class="value">$0</span>
                            </div>
                            <div class="breakdown-item">
                                <span class="label">Monthly fee:</span>
                                <span class="value">$0</span>
                            </div>
                            <div class="breakdown-item">
                                <span class="label">Withdrawal fee:</span>
                                <span class="value">Network gas only</span>
                            </div>
                        </div>

                        <p class="fee-note">TRON network fees (gas) are covered by us for incoming transactions. Withdrawals
                            use standard TRON network fees, which are super cheap anyway.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="floating-text-wrapper">
            <p class="floating-text">Pretty nice huh?</p>
        </div>

        <!-- PARTNERSHIP SECTION -->
        <div id="partnership" class="scroll-space" ref="section3">
            <div class="content-section partnership-content">
                <div class="section-header">
                    <span class="section-number">03</span>
                    <h2>Wanna Partner Up?</h2>
                </div>

                <div class="partnership-layout">
                    <div class="partnership-info">
                        <h3>We're looking for creators</h3>
                        <p>If you're a streamer, content creator, or running a community, let's talk. We offer custom
                            integrations, better rates, and dedicated support for partners.</p>

                        <ul class="partnership-perks">
                            <li>Reduced platform fees</li>
                            <li>Priority support</li>
                            <li>Custom features for your community</li>
                            <li>Early access to new stuff</li>
                        </ul>
                    </div>

                    <form class="contact-form" @submit.prevent="submitPartnershipForm">
                        <input type="text" v-model="partnershipForm.name" placeholder="Your name" required />
                        <input type="email" v-model="partnershipForm.email" placeholder="Email address" required />
                        <input type="text" v-model="partnershipForm.platform"
                            placeholder="Platform (Twitch, YouTube, etc.)" />
                        <textarea v-model="partnershipForm.message" placeholder="Tell us about your project..." rows="5"
                            required></textarea>
                        <button type="submit" class="submit-btn">
                            {{ partnershipForm.submitting ? 'Sending...' : 'Send Message' }}
                        </button>
                        <p v-if="partnershipForm.success" class="form-success">Thanks! We'll get back to you soon.</p>
                        <p v-if="partnershipForm.error" class="form-error">{{ partnershipForm.error }}</p>
                    </form>
                </div>
            </div>
        </div>

        <div class="floating-text-wrapper">
            <p class="floating-text">Simple as that</p>
        </div>

        <!-- FAQ SECTION -->
        <div id="faq" class="scroll-space" ref="section4">
            <div class="content-section faq-content">
                <div class="section-header">
                    <span class="section-number">04</span>
                    <h2>FAQ</h2>
                </div>

                <div class="faq-list">
                    <div v-for="(item, index) in faqItems" :key="index" class="faq-item" :class="{ 'active': item.open }"
                        @click="toggleFaq(index)">
                        <div class="faq-question">
                            <h3>{{ item.question }}</h3>
                            <span class="faq-icon">{{ item.open ? '−' : '+' }}</span>
                        </div>
                        <transition name="faq-answer">
                            <div v-if="item.open" class="faq-answer">
                                <p>{{ item.answer }}</p>
                            </div>
                        </transition>
                    </div>
                </div>
            </div>
        </div>

        <div class="floating-text-wrapper">
            <p class="floating-text">Still got questions?</p>
        </div>

        <!-- SUPPORT SECTION -->
        <div id="support" class="scroll-space" ref="section5">
            <div class="content-section support-content">
                <div class="section-header">
                    <span class="section-number">05</span>
                    <h2>Get in Touch</h2>
                </div>

                <div class="support-layout">
                    <div class="support-info">
                        <h3>Need help?</h3>
                        <p>We're here. Drop us a message and we'll get back to you ASAP.</p>

                        <div class="contact-methods">
                            <div class="method">
                                <span class="method-label">Email:</span>
                                <a href="mailto:support@cryptoalerts.io">support@cryptoalerts.io</a>
                            </div>
                            <div class="method">
                                <span class="method-label">Response time:</span>
                                <span>Usually under 2 hours in CET daytime</span>
                            </div>
                        </div>
                    </div>

                    <form class="contact-form" @submit.prevent="submitSupportForm">
                        <input type="text" v-model="supportForm.name" placeholder="Your name" required />
                        <input type="email" v-model="supportForm.email" placeholder="Email address" required />
                        <input type="text" v-model="supportForm.subject" placeholder="Subject" required />
                        <textarea v-model="supportForm.message" placeholder="What's up?" rows="6" required></textarea>
                        <button type="submit" class="submit-btn">
                            {{ supportForm.submitting ? 'Sending...' : 'Send Message' }}
                        </button>
                        <p v-if="supportForm.success" class="form-success">Message sent! We'll reply soon.</p>
                        <p v-if="supportForm.error" class="form-error">{{ supportForm.error }}</p>
                    </form>
                </div>
            </div>
        </div>

        <div class="scroll-space empty-space" ref="section6"></div>

        <footer class="footer">
            <div class="footer-content">
                <p>&copy; 2025 CryptoAlerts. All rights reserved.</p>
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
                "but may be better...",
                "what's next?",
                "feel free to ask",
                // "what do you think, chat?",
                // "what do you think, chat?",
                "r we starting or sum?",
                "r we starting or sum?",
            ],
            ticking: false,
            onScrollBound: null,
            onResizeBound: null,
            isMobileMenuOpen: false,
            windowWidth: window.innerWidth,

            // FAQ Data
            faqItems: [
                {
                    question: "How do I get started?",
                    answer: "Sign up, create your donation page, and you're good to go. Takes like 2 minutes. Get your personal link, compllete simple moderation and start accepting donations immediately.",
                    open: false
                },
                {
                    question: "What cryptocurrencies do you support?",
                    answer: "Currently we support USDT on the TRON network (TRC20). It's fast, cheap, and widely used. More coins coming soon based on community feedback.",
                    open: false
                },
                {
                    question: "How fast are transactions?",
                    answer: "TRON is crazy fast. Transactions typically confirm in under a minute. You'll see the donation hit your dashboard almost instantly.",
                    open: false
                },
                {
                    question: "How is withdrawal process goes?",
                    answer: "You can withdraw balance starting from 50 USDT. If you are willing to get lower commisions this limit may increace.",
                    open: false
                },
                {
                    question: "Is this safe?",
                    answer: "100%. We provide AML checks on our side, so you won't get troubles. Your private keys stay private. We never have access to your funds.",
                    open: false
                },
                {
                    question: "What about chargebacks?",
                    answer: "This is crypto, baby. No chargebacks. Once a transaction is confirmed on the blockchain, it's final. That's the beauty of it.",
                    open: false
                },
                {
                    question: "Do I need technical knowledge?",
                    answer: "Nah. If you can copy-paste a link, you're good. We made it as simple as possible. The complex blockchain stuff happens behind the scenes.",
                    open: false
                },
                {
                    question: "What if I have an issue?",
                    answer: "Hit up our support team. We respond ASAP and actually help. We have the bot in support but you can easily avoid it if you really need that support.",
                    open: false
                }
            ],

            // Partnership Form
            partnershipForm: {
                name: '',
                email: '',
                platform: '',
                message: '',
                submitting: false,
                success: false,
                error: ''
            },

            // Support Form
            supportForm: {
                name: '',
                email: '',
                subject: '',
                message: '',
                submitting: false,
                success: false,
                error: ''
            }
        };
    },
    computed: {
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
            this.windowWidth = window.innerWidth;
            this.updateDisplayedText();
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

        toggleFaq(index) {
            this.faqItems[index].open = !this.faqItems[index].open;
        },

        async submitPartnershipForm() {
            this.partnershipForm.submitting = true;
            this.partnershipForm.error = '';
            this.partnershipForm.success = false;

            try {
                // Здесь будет твой API эндпоинт
                // const response = await fetch('/api/partnership', {
                //     method: 'POST',
                //     body: JSON.stringify(this.partnershipForm)
                // });

                // Симуляция отправки
                await new Promise(resolve => setTimeout(resolve, 1500));

                this.partnershipForm.success = true;
                this.partnershipForm.name = '';
                this.partnershipForm.email = '';
                this.partnershipForm.platform = '';
                this.partnershipForm.message = '';
            } catch (error) {
                this.partnershipForm.error = 'Something went wrong. Try again?';
            } finally {
                this.partnershipForm.submitting = false;
            }
        },

        async submitSupportForm() {
            this.supportForm.submitting = true;
            this.supportForm.error = '';
            this.supportForm.success = false;

            try {
                // Здесь будет твой API эндпоинт
                // const response = await fetch('/api/support', {
                //     method: 'POST',
                //     body: JSON.stringify(this.supportForm)
                // });

                // Симуляция отправки
                await new Promise(resolve => setTimeout(resolve, 1500));

                this.supportForm.success = true;
                this.supportForm.name = '';
                this.supportForm.email = '';
                this.supportForm.subject = '';
                this.supportForm.message = '';
            } catch (error) {
                this.supportForm.error = 'Oops, something broke. Try again?';
            } finally {
                this.supportForm.submitting = false;
            }
        }
    },
};
</script>

<style>
@import url('https://fonts.cdnfonts.com/css/sf-pro-display');

html {
    scroll-behavior: smooth;
}

* {
    box-sizing: border-box;
}

.page-wrapper {
    min-height: 600vh;
}

/* Video Background */
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
    font-size: max(10vh, 11vw);
    line-height: 100%;
    font-weight: 900;
    font-family: "Arial Black", Arial, sans-serif;
    color: #000;
    margin: 0;
    text-align: center;
    text-transform: uppercase;
    pointer-events: none;
    white-space: pre-line;
}

.cutout-text.justify-text {
    text-align: justify;
    text-align-last: justify;
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

/* Navigation Styles */
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
    font-size: min(4vw, .875rem);
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

/* Scroll Spaces */
.scroll-space {
    position: relative;
    z-index: 10;
    min-height: 100vh;
    min-height: 100svh;
    margin-top: 100vh;
    margin-top: 100svh;
    padding: 6rem 2rem;
    background: #1b1b1b;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Content Section Styling */
.content-section {
    max-width: 1200px;
    width: 100%;
    color: #fff;
    font-family: "SF Pro Display", sans-serif;
}

.section-header {
    display: flex;
    align-items: baseline;
    gap: 1.5rem;
    margin-bottom: 4rem;
}

.section-number {
    font-size: 0.875rem;
    color: rgba(255, 255, 255, 0.4);
    font-weight: 300;
    letter-spacing: 0.2em;
}

.section-header h2 {
    font-size: clamp(2.5rem, 6vw, 4rem);
    font-weight: 700;
    margin: 0;
    letter-spacing: -0.02em;
}

.section-description {
    font-size: clamp(1rem, 2vw, 1.15rem);
    line-height: 1.8;
    color: rgba(255, 255, 255, 0.7);
    max-width: 800px;
    margin: -2rem 0 3rem 0;
    font-weight: 300;
    letter-spacing: 0.01em;
}

@media (max-width: 768px) {
    .section-description {
        margin: -1.5rem 0 2.5rem 0;
        font-size: 0.95rem;
    }
}


/* FEATURES Section */
.feature-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

.feature-item {
    padding: 2rem;
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    transition: all 0.3s ease;
}

.feature-item:hover {
    background: rgba(255, 255, 255, 0.05);
    border-color: rgba(255, 106, 0, 0.3);
    transform: translateY(-4px);
}

.feature-item.highlight {
    border-color: rgba(255, 106, 0, 0.4);
    background: rgba(255, 106, 0, 0.05);
}

.feature-item h3 {
    font-size: 1.25rem;
    font-weight: 600;
    margin: 0 0 1rem 0;
    color: #fff;
}

.feature-item p {
    font-size: 0.95rem;
    line-height: 1.6;
    color: rgba(255, 255, 255, 0.7);
    margin: 0;
}

/* FEES Section */
.fees-layout {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 4rem;
    align-items: center;
}

.fee-visual {
    display: flex;
    align-items: center;
    justify-content: center;
}

.big-seven {
    font-size: clamp(8rem, 20vw, 15rem);
    font-weight: 900;
    line-height: 1;
    color: #ff6a00;
    font-family: "Arial Black", Arial, sans-serif;
}

.big-seven img {
    width: 25vw;
}

.percent {
    font-size: 0.5em;
    vertical-align: super;
}

.fee-details h3 {
    font-size: clamp(1.5rem, 3vw, 2.5rem);
    margin: 0 0 1rem 0;
    font-weight: 600;
}

.fee-details>p {
    font-size: 1.1rem;
    line-height: 1.7;
    color: rgba(255, 255, 255, 0.8);
    margin-bottom: 2rem;
}

.fee-breakdown {
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 12px;
    padding: 2rem;
    margin: 2rem 0;
}

.breakdown-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.75rem 0;
    border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.breakdown-item:last-child {
    border-bottom: none;
}

.breakdown-item .label {
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.95rem;
}

.breakdown-item .value {
    color: #fff;
    font-weight: 600;
    font-size: 1.1rem;
}

.fee-note {
    font-size: 0.875rem;
    color: rgba(255, 255, 255, 0.5);
    line-height: 1.6;
    margin: 1.5rem 0 0 0;
}

/* PARTNERSHIP Section */
.partnership-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
}

.partnership-info h3 {
    font-size: clamp(1.5rem, 3vw, 2rem);
    margin: 0 0 1rem 0;
}

.partnership-info>p {
    font-size: 1.05rem;
    line-height: 1.7;
    color: rgba(255, 255, 255, 0.8);
    margin-bottom: 2rem;
}

.partnership-perks {
    list-style: none;
    padding: 0;
    margin: 0;
}

.partnership-perks li {
    padding: 0.75rem 0;
    padding-left: 1.5rem;
    position: relative;
    color: rgba(255, 255, 255, 0.8);
    font-size: 1rem;
}

.partnership-perks li::before {
    content: "→";
    position: absolute;
    left: 0;
    color: #ff6a00;
    font-weight: 600;
}

/* Contact Forms */
.contact-form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.contact-form input,
.contact-form textarea {
    width: 100%;
    padding: 1rem 1.25rem;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 8px;
    color: #fff;
    font-family: "SF Pro Display", sans-serif;
    font-size: 0.95rem;
    transition: all 0.3s ease;
}

.contact-form input:focus,
.contact-form textarea:focus {
    outline: none;
    border-color: #ff6a00;
    background: rgba(255, 255, 255, 0.08);
}

.contact-form input::placeholder,
.contact-form textarea::placeholder {
    color: rgba(255, 255, 255, 0.4);
}

.contact-form textarea {
    resize: vertical;
    min-height: 120px;
}

.submit-btn {
    padding: 1rem 2rem;
    background: linear-gradient(135deg, #ff6a00 0%, #ff8c42 100%);
    border: none;
    border-radius: 8px;
    color: #fff;
    font-family: "SF Pro Display", sans-serif;
    font-size: 1rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    cursor: pointer;
    transition: all 0.3s ease;
}

.submit-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(255, 106, 0, 0.3);
}

.submit-btn:active {
    transform: translateY(0);
}

.form-success {
    color: #4ade80;
    font-size: 0.9rem;
    margin: 0;
}

.form-error {
    color: #f87171;
    font-size: 0.9rem;
    margin: 0;
}

/* FAQ Section */
.faq-list {
    max-width: 900px;
}

.faq-item {
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    cursor: pointer;
    transition: all 0.3s ease;
}

.faq-item:last-child {
    border-bottom: none;
}

.faq-question {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 0;
    gap: 2rem;
}

.faq-question h3 {
    font-size: 1.15rem;
    font-weight: 500;
    margin: 0;
    color: rgba(255, 255, 255, 0.9);
    transition: color 0.3s ease;
}

.faq-item:hover .faq-question h3,
.faq-item.active .faq-question h3 {
    color: #ff6a00;
}

.faq-icon {
    font-size: 1.5rem;
    color: rgba(255, 255, 255, 0.5);
    font-weight: 300;
    transition: color 0.3s ease;
}

.faq-item.active .faq-icon {
    color: #ff6a00;
}

.faq-answer {
    padding-bottom: 1.5rem;
}

.faq-answer p {
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.7;
    margin: 0;
    font-size: 0.95rem;
}

.faq-answer-enter-active,
.faq-answer-leave-active {
    transition: all 0.3s ease;
}

.faq-answer-enter-from,
.faq-answer-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}

/* SUPPORT Section */
.support-layout {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 4rem;
}

.support-info h3 {
    font-size: clamp(1.5rem, 3vw, 2rem);
    margin: 0 0 1rem 0;
}

.support-info>p {
    font-size: 1.05rem;
    line-height: 1.7;
    color: rgba(255, 255, 255, 0.8);
    margin-bottom: 2rem;
}

.contact-methods {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.method {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
}

.method-label {
    font-size: 0.85rem;
    color: rgba(255, 255, 255, 0.5);
    text-transform: uppercase;
    letter-spacing: 0.1em;
}

.method a {
    color: #ff6a00;
    text-decoration: none;
    font-size: 1.1rem;
    transition: opacity 0.3s ease;
}

.method a:hover {
    opacity: 0.8;
}

.method span:not(.method-label) {
    color: rgba(255, 255, 255, 0.8);
    font-size: 1.05rem;
}


/* Hamburger Button */
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

/* Mobile Menu */
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

.mobile-menu-enter-from .mobile-menu-content,
.mobile-menu-leave-to .mobile-menu-content {
    transform: translateX(100%);
}

/* Footer */
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

/* Floating Text - Giant Watermark Style (Centered) */
.floating-text-wrapper {
    position: relative;
    height: 0;
    z-index: 15;
    pointer-events: none;
    top: 50%;
    left: 0;
    right: 0;
    width: 100%;
}

.floating-text {
    position: sticky;
    top: 50%;
    /* transform: translateY(-10%); */
    margin: 0 auto;
    padding: 0;

    font-family: "Arial Black", Arial, sans-serif;
    font-size: clamp(3rem, 12vw, 8rem);
    font-weight: 900;
    letter-spacing: -0.03em;
    line-height: 1;

    color: rgba(0, 0, 0, 0.08);
    text-transform: uppercase;

    pointer-events: none;
    width: fit-content;
    text-align: center;

    transition: all 0.6s ease;
}

/* Убрал смещения для left/right - теперь все строго по центру */
.floating-text-wrapper:nth-child(odd) .floating-text,
.floating-text-wrapper:nth-child(even) .floating-text {
    margin: 0 auto;
}

@media (max-width: 768px) {
    .floating-text {
        font-size: clamp(2rem, 15vw, 5rem);
    }

    .floating-text-wrapper:nth-child(odd) .floating-text {
        padding-left: 5%;
    }

    .floating-text-wrapper:nth-child(even) .floating-text {
        padding-right: 5%;
    }
}



/* Mobile & Tablet Responsive */
@media (max-width: 1024px) {

    .fees-layout,
    .partnership-layout,
    .support-layout {
        grid-template-columns: 1fr;
        gap: 3rem;
    }

    .big-seven {
        font-size: 10rem;
    }

    .big-seven img {
        width: 30vw;
    }

}

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

    .section-header {
        flex-direction: column;
        gap: 0.5rem;
        margin-bottom: 2.5rem;
    }

    .feature-grid {
        grid-template-columns: 1fr;
        gap: 1.5rem;
    }

    .feature-item {
        padding: 1.5rem;
    }

    .scroll-space {
        padding: 4rem 1.5rem;
    }

    .big-seven img {
        width: 50vw;
    }

}

@media (max-width: 490px) {

    .big-seven {
        font-size: 8rem;
    }

    .cutout-text {
        font-size: 16vw;
    }
}

@media (min-width: 769px) {
    .mobile-nav {
        display: none !important;
    }

    .desktop-nav {
        display: flex !important;
    }
}
</style>
