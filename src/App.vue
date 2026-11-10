<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const menuOpen = ref(false)
const menuToggle = ref(null)

function closeMenu() {
  menuOpen.value = false
}

function handleGlobalKeydown(event) {
  if (event.key === 'Escape' && menuOpen.value) {
    closeMenu()
    menuToggle.value?.focus()
  }
}

function handleOutsidePointer(event) {
  if (event.target instanceof Element && !event.target.closest('.site-header')) {
    closeMenu()
  }
}

function handleViewportResize() {
  if (window.innerWidth > 700) {
    closeMenu()
  }
}

onMounted(() => {
  document.addEventListener('keydown', handleGlobalKeydown)
  document.addEventListener('pointerdown', handleOutsidePointer)
  window.addEventListener('resize', handleViewportResize)
})

onUnmounted(() => {
  document.removeEventListener('keydown', handleGlobalKeydown)
  document.removeEventListener('pointerdown', handleOutsidePointer)
  window.removeEventListener('resize', handleViewportResize)
})

const navigation = [
  { label: 'Home', href: '#home' },
  { label: 'Services', href: '#services' },
  { label: 'Features', href: '#features' },
  { label: 'Pricing', href: '#pricing' },
  { label: 'About', href: '#about' },
  { label: 'Contact', href: '#contact' },
]

const services = [
  {
    icon: 'cloud',
    title: 'Cloud computing',
    description:
      'Launch virtual machines in seconds and scale your compute power as your ideas take off.',
    detail: 'Flexible compute',
  },
  {
    icon: 'database',
    title: 'Cloud storage',
    description:
      'Keep every file, backup, and data set safe with fast, resilient object storage.',
    detail: 'Secure by design',
  },
  {
    icon: 'server',
    title: 'Cloud hosting',
    description:
      'Deploy your websites and apps on infrastructure built for speed, uptime, and growth.',
    detail: 'Always online',
  },
]

const features = [
  {
    icon: 'shield',
    title: 'Security at every layer',
    description:
      'Your data stays protected with encryption, isolated networks, and thoughtful access controls.',
  },
  {
    icon: 'expand',
    title: 'Scale without limits',
    description:
      'Add capacity when you need it, and keep your infrastructure lean when you don’t.',
  },
  {
    icon: 'pulse',
    title: 'Reliability you can count on',
    description:
      'Built-in monitoring and resilient systems help your services stay steady under pressure.',
  },
  {
    icon: 'globe',
    title: 'High availability, everywhere',
    description:
      'Deploy across regions and keep your applications close to the people who use them.',
  },
]

const plans = [
  {
    name: 'Starter',
    description: 'Everything you need to get your idea off the ground.',
    price: '$19',
    period: '/ month',
    features: ['2 vCPU compute', '50 GB secure storage', 'Community support'],
  },
  {
    name: 'Professional',
    description: 'More power and flexibility for growing teams.',
    price: '$79',
    period: '/ month',
    features: ['8 vCPU compute', '500 GB secure storage', 'Priority support'],
    popular: true,
  },
  {
    name: 'Enterprise',
    description: 'Advanced infrastructure for ambitious businesses.',
    price: 'Custom',
    period: 'let’s talk',
    features: ['Custom compute', 'Flexible storage', 'Dedicated support'],
  },
]
</script>

<template>
  <svg class="icon-library" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <symbol id="icon-cloud" viewBox="0 0 24 24">
      <path d="M7.5 18.5h10a4.5 4.5 0 0 0 .4-9A6.5 6.5 0 0 0 5.4 11a3.8 3.8 0 0 0 2.1 7.5Z" />
      <path d="m9 14 3-3 3 3m-3-3v7" />
    </symbol>
    <symbol id="icon-database" viewBox="0 0 24 24">
      <ellipse cx="12" cy="5" rx="8" ry="3" />
      <path d="M4 5v14c0 1.7 3.6 3 8 3s8-1.3 8-3V5M4 12c0 1.7 3.6 3 8 3s8-1.3 8-3" />
    </symbol>
    <symbol id="icon-server" viewBox="0 0 24 24">
      <rect x="3" y="3" width="18" height="8" rx="2" />
      <rect x="3" y="13" width="18" height="8" rx="2" />
      <path d="M7 7h.01M7 17h.01M11 7h6M11 17h6" />
    </symbol>
    <symbol id="icon-shield" viewBox="0 0 24 24">
      <path d="M12 22s8-4 8-11V5l-8-3-8 3v6c0 7 8 11 8 11Z" />
      <path d="m9 12 2 2 4-4" />
    </symbol>
    <symbol id="icon-expand" viewBox="0 0 24 24">
      <path d="M8 3H5a2 2 0 0 0-2 2v3m13-5h3a2 2 0 0 1 2 2v3M3 16v3a2 2 0 0 0 2 2h3m13-5v3a2 2 0 0 1-2 2h-3M8 12h8m-4-4v8" />
    </symbol>
    <symbol id="icon-pulse" viewBox="0 0 24 24">
      <path d="M3 12h4l3-8 4 16 3-8h4" />
    </symbol>
    <symbol id="icon-globe" viewBox="0 0 24 24">
      <circle cx="12" cy="12" r="10" />
      <path d="M2 12h20M12 2a15 15 0 0 1 0 20 15 15 0 0 1 0-20Z" />
    </symbol>
    <symbol id="icon-mail" viewBox="0 0 24 24">
      <rect x="3" y="5" width="18" height="14" rx="2" />
      <path d="m3 7 9 6 9-6" />
    </symbol>
    <symbol id="icon-check" viewBox="0 0 24 24">
      <path d="m5 12 4 4L19 6" />
    </symbol>
    <symbol id="icon-arrow" viewBox="0 0 24 24">
      <path d="M5 12h14m-7-7 7 7-7 7" />
    </symbol>
    <symbol id="icon-menu" viewBox="0 0 24 24">
      <path d="M4 7h16M4 12h16M4 17h16" />
    </symbol>
    <symbol id="icon-close" viewBox="0 0 24 24">
      <path d="m6 6 12 12M18 6 6 18" />
    </symbol>
  </svg>

  <header class="site-header">
    <nav class="nav shell" aria-label="Main navigation">
      <a class="brand" href="#home" aria-label="CloudNova home" @click="menuOpen = false">
        <span class="brand-mark" aria-hidden="true">
          <svg viewBox="0 0 32 32" fill="none">
            <path d="M8 20.5h15a5 5 0 0 0 .3-10A7 7 0 0 0 10 12a4.3 4.3 0 0 0-2 8.5Z" />
            <path d="m13 16 3-3 3 3m-3-3v7" />
          </svg>
        </span>
        <span>cloud<span class="brand-light">nova</span></span>
      </a>

      <button
        ref="menuToggle"
        class="menu-toggle"
        type="button"
        :aria-expanded="menuOpen"
        aria-controls="primary-links"
        :aria-label="menuOpen ? 'Close navigation menu' : 'Open navigation menu'"
        @click="menuOpen = !menuOpen"
      >
        <svg class="icon" aria-hidden="true">
          <use :href="menuOpen ? '#icon-close' : '#icon-menu'" />
        </svg>
      </button>

      <div id="primary-links" class="nav-links" :class="{ 'is-open': menuOpen }">
        <a
          v-for="item in navigation"
          :key="item.label"
          :href="item.href"
          @click="closeMenu"
        >
          {{ item.label }}
        </a>
        <a class="button button-small nav-cta" href="#contact" @click="closeMenu">
          Get started <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg>
        </a>
      </div>
    </nav>
  </header>

  <main>
    <section id="home" class="hero section" aria-labelledby="hero-title">
      <div class="hero-glow hero-glow-one" aria-hidden="true"></div>
      <div class="hero-glow hero-glow-two" aria-hidden="true"></div>
      <div class="hero-layout shell">
        <div class="hero-copy">
          <div class="eyebrow"><span class="status-dot"></span> Cloud infrastructure, reimagined</div>
          <h1 id="hero-title">Your next big idea deserves <span>better cloud.</span></h1>
          <p class="hero-description">
            The reliable, effortless cloud platform built to take your business from first
            deploy to what’s next.
          </p>
          <div class="hero-actions">
            <a class="button" href="#pricing">
              Explore the platform <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg>
            </a>
            <a class="text-link" href="#services">Discover our services</a>
          </div>
          <div class="hero-proof">
            <div class="avatar-stack" aria-hidden="true">
              <span>J</span><span>M</span><span>A</span><span>+</span>
            </div>
            <p><strong>Built for builders</strong><br />Trusted by teams moving forward</p>
          </div>
        </div>

        <div
          class="hero-visual"
          role="img"
          aria-label="Illustration of connected cloud infrastructure"
        >
          <div class="visual-orbit orbit-outer"></div>
          <div class="visual-orbit orbit-inner"></div>
          <div class="visual-node node-top"><span></span>Compute</div>
          <div class="visual-node node-bottom"><span></span>Storage</div>
          <div class="visual-card">
            <div class="visual-card-top">
              <span class="window-dots"><i></i><i></i><i></i></span>
              <span>cloudnova / overview</span>
              <span class="live-pill"><i></i> Live</span>
            </div>
            <svg class="cloud-art" viewBox="0 0 480 340" fill="none" role="presentation">
              <defs>
                <linearGradient id="cloud-fill" x1="147" y1="97" x2="332" y2="265" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#96A8FF" stop-opacity=".26" />
                  <stop offset="1" stop-color="#A65EFF" stop-opacity=".1" />
                </linearGradient>
                <linearGradient id="cloud-stroke" x1="115" y1="88" x2="362" y2="267" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#A9B8FF" />
                  <stop offset=".52" stop-color="#878BFF" />
                  <stop offset="1" stop-color="#C77BFF" />
                </linearGradient>
                <filter id="cloud-shadow" x="80" y="72" width="330" height="235" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse">
                  <feGaussianBlur stdDeviation="18" />
                </filter>
              </defs>
              <ellipse cx="244" cy="190" rx="143" ry="92" fill="#795BFF" fill-opacity=".26" filter="url(#cloud-shadow)" />
              <path d="M154 249h166a48 48 0 0 0 3-96 73 73 0 0 0-139-20 47 47 0 0 0-30 88" fill="url(#cloud-fill)" stroke="url(#cloud-stroke)" stroke-width="2" />
              <path d="M184 196h112M240 160v74m-27-48 27-27 27 27" stroke="#E3E7FF" stroke-linecap="round" stroke-linejoin="round" stroke-width="3" />
              <circle cx="240" cy="235" r="5" fill="#D9DFFF" />
              <path d="M240 240v42m-82 0h164M158 282v17m164-17v17" stroke="#8E9BFF" stroke-opacity=".72" stroke-width="1.5" />
              <rect x="126" y="299" width="64" height="22" rx="7" fill="#726BFF" fill-opacity=".22" stroke="#8C8FFF" stroke-opacity=".65" />
              <rect x="208" y="299" width="64" height="22" rx="7" fill="#726BFF" fill-opacity=".22" stroke="#8C8FFF" stroke-opacity=".65" />
              <rect x="290" y="299" width="64" height="22" rx="7" fill="#A064FF" fill-opacity=".22" stroke="#BD8BFF" stroke-opacity=".65" />
              <circle cx="158" cy="310" r="3" fill="#A8B4FF" /><circle cx="240" cy="310" r="3" fill="#A8B4FF" /><circle cx="322" cy="310" r="3" fill="#C5A3FF" />
              <path d="M80 142h31m258 0h31M97 240h28m230 0h28" stroke="#8F9BFF" stroke-opacity=".45" stroke-dasharray="3 5" />
              <circle cx="80" cy="142" r="4" fill="#AEB7FF" /><circle cx="400" cy="142" r="4" fill="#C595FF" />
            </svg>
            <div class="visual-metric">
              <span class="metric-icon"><svg class="icon" aria-hidden="true"><use href="#icon-pulse" /></svg></span>
              <span><strong>99.99%</strong><small>uptime this month</small></span>
              <span class="metric-trend">↗ 0.02%</span>
            </div>
          </div>
          <div class="floating-badge"><span class="badge-check"><svg class="icon" aria-hidden="true"><use href="#icon-check" /></svg></span><span><strong>All systems go</strong><small>Across every region</small></span></div>
          <span class="sparkle sparkle-one" aria-hidden="true">✦</span>
          <span class="sparkle sparkle-two" aria-hidden="true">✧</span>
        </div>
      </div>
      <div class="hero-bottom shell">
        <span>POWERING WHAT’S NEXT</span>
        <div class="trust-logos" aria-label="Trusted by innovative teams">
          <span>◈ &nbsp;northstar</span><span>✳ &nbsp;vertex</span><span>⌘ &nbsp;layer</span><span>◉ &nbsp;arcadia</span>
        </div>
      </div>
    </section>

    <section id="services" class="section section-space" aria-labelledby="services-title">
      <div class="shell">
        <div class="section-heading">
          <span class="eyebrow">ONE PLATFORM. MORE POSSIBILITIES.</span>
          <h2 id="services-title">Everything you need to <span>build forward.</span></h2>
          <p>Powerful cloud essentials, without the unnecessary complexity.</p>
        </div>
        <div class="service-grid">
          <article v-for="(service, index) in services" :key="service.title" class="service-card">
            <div class="card-icon" :class="`tone-${index + 1}`">
              <svg class="icon" aria-hidden="true"><use :href="`#icon-${service.icon}`" /></svg>
            </div>
            <h3>{{ service.title }}</h3>
            <p>{{ service.description }}</p>
            <a class="card-link" href="#contact">{{ service.detail }} <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg></a>
          </article>
        </div>
      </div>
    </section>

    <section id="features" class="section section-space features-section" aria-labelledby="features-title">
      <div class="shell features-layout">
        <div class="features-intro">
          <span class="eyebrow">CLOUD YOU CAN COUNT ON</span>
          <h2 id="features-title">Serious infrastructure.<br /><span>Zero drama.</span></h2>
          <p>
            Spend less time managing servers and more time making things people love. We
            handle the hard parts, so you can focus on the next big thing.
          </p>
          <a class="text-link" href="#about">A little more about us <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg></a>
        </div>
        <div class="features-grid">
          <article v-for="feature in features" :key="feature.title" class="feature-item">
            <div class="feature-icon"><svg class="icon" aria-hidden="true"><use :href="`#icon-${feature.icon}`" /></svg></div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </article>
        </div>
      </div>
    </section>

    <section id="pricing" class="section section-space pricing-section" aria-labelledby="pricing-title">
      <div class="shell">
        <div class="section-heading">
          <span class="eyebrow">SIMPLE, TRANSPARENT PRICING</span>
          <h2 id="pricing-title">Room to grow. <span>Not to guess.</span></h2>
          <p>Choose a starting point that works for you. Change it whenever you need.</p>
          <div class="sample-note"><span>ⓘ</span> Fictional sample pricing for illustrative purposes only.</div>
        </div>
        <div class="pricing-grid">
          <article v-for="plan in plans" :key="plan.name" class="price-card" :class="{ featured: plan.popular }">
            <div v-if="plan.popular" class="popular-label">MOST POPULAR</div>
            <h3>{{ plan.name }}</h3>
            <p class="plan-description">{{ plan.description }}</p>
            <div class="plan-price"><strong>{{ plan.price }}</strong><span>{{ plan.period }}</span></div>
            <a class="button" :class="plan.popular ? 'button-primary' : 'button-quiet'" href="#contact">
              {{ plan.name === 'Enterprise' ? 'Talk to our team' : 'Get started' }}
              <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg>
            </a>
            <div class="plan-divider"></div>
            <span class="included-label">WHAT’S INCLUDED</span>
            <ul>
              <li v-for="item in plan.features" :key="item">
                <svg class="icon" aria-hidden="true"><use href="#icon-check" /></svg>{{ item }}
              </li>
            </ul>
          </article>
        </div>
      </div>
    </section>

    <section id="about" class="section section-space about-section" aria-labelledby="about-title">
      <div class="shell about-card">
        <div class="about-art" aria-hidden="true">
          <div class="about-orbit about-orbit-one"></div>
          <div class="about-orbit about-orbit-two"></div>
          <div class="about-core"><svg class="icon"><use href="#icon-cloud" /></svg></div>
          <span class="about-star star-a">✦</span><span class="about-star star-b">✧</span><span class="about-star star-c">·</span>
        </div>
        <div class="about-copy">
          <span class="eyebrow">A BETTER WAY TO CLOUD</span>
          <h2 id="about-title">Big cloud energy.<br /><span>Small-team attention.</span></h2>
          <p>
            CloudNova is a fictional cloud company with a simple belief: infrastructure
            should help good ideas move faster, not get in their way. We’re here to make
            powerful, dependable cloud tools feel refreshingly human.
          </p>
          <a class="text-link" href="#contact">Let’s build something <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg></a>
        </div>
      </div>
    </section>

    <section id="contact" class="section contact-section" aria-labelledby="contact-title">
      <div class="shell contact-card">
        <div class="contact-glow" aria-hidden="true"></div>
        <span class="eyebrow">LET’S MAKE IT HAPPEN</span>
        <h2 id="contact-title">Your next chapter<br />starts <span>in the cloud.</span></h2>
        <p>Have a question or a big idea? We’d love to hear from you.</p>
        <a class="button" href="mailto:hello@cloudnova.example">
          Say hello <svg class="icon" aria-hidden="true"><use href="#icon-arrow" /></svg>
        </a>
        <div class="contact-details" role="group" aria-label="Sample contact information">
          <div class="contact-detail-item">
            <svg class="icon" aria-hidden="true"><use href="#icon-mail" /></svg>
            <span class="contact-detail-copy">
              <span class="contact-detail-label">Email</span>
              <a href="mailto:hello@cloudnova.example">hello@cloudnova.example</a>
            </span>
          </div>
          <address class="contact-detail-item">
            <svg class="icon" aria-hidden="true"><use href="#icon-globe" /></svg>
            <span class="contact-detail-copy">
              <span class="contact-detail-label">Location</span>
              <span>San Francisco, CA · Remote everywhere</span>
            </span>
          </address>
        </div>
        <small class="sample-note contact-note">Sample contact details for this fictional company.</small>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <div class="shell footer-main">
      <a class="brand" href="#home" aria-label="CloudNova home">
        <span class="brand-mark" aria-hidden="true">
          <svg viewBox="0 0 32 32" fill="none">
            <path d="M8 20.5h15a5 5 0 0 0 .3-10A7 7 0 0 0 10 12a4.3 4.3 0 0 0-2 8.5Z" />
            <path d="m13 16 3-3 3 3m-3-3v7" />
          </svg>
        </span>
        <span>cloud<span class="brand-light">nova</span></span>
      </a>
      <p>Cloud made for the next big thing.</p>
      <nav class="footer-links" aria-label="Footer navigation">
        <a v-for="item in navigation" :key="item.label" :href="item.href">{{ item.label }}</a>
      </nav>
    </div>
    <div class="shell footer-bottom">
      <span>© 2026 CloudNova. All rights reserved.</span>
      <span>Fictional company · Sample website</span>
    </div>
  </footer>
</template>
