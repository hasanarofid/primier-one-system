<script setup>
import { Head, Link, usePage } from '@inertiajs/vue3';
import { 
  Phone, 
  ArrowUpRight, 
  CheckCircle, 
  Layers, 
  ChevronRight,
  Trophy,
  MapPin,
  Mail
} from '@lucide/vue';

const props = defineProps({
  settings: {
    type: Object,
    required: true
  },
  navigation: {
    type: Array,
    required: true
  },
  page: {
    type: Object,
    default: null
  },
  posts: {
    type: Array,
    default: () => []
  }
});

const pageData = usePage();
const user = pageData.props.auth?.user;
</script>

<template>
  <Head :title="page?.title || 'Premier One Motorsport'" />

  <div class="min-h-screen bg-[#0a0510] text-slate-100 font-sans selection:bg-purple-500 selection:text-white relative overflow-hidden">
    <!-- Background Glow Blobs for Dark Racing Vibe -->
    <div class="absolute top-[-20%] left-[-10%] w-[600px] h-[600px] rounded-full bg-purple-900/20 blur-[120px] pointer-events-none"></div>
    <div class="absolute bottom-[-10%] right-[-10%] w-[600px] h-[600px] rounded-full bg-indigo-900/20 blur-[120px] pointer-events-none"></div>

    <!-- Navbar -->
    <nav class="sticky top-0 z-50 bg-[#0a0510]/80 backdrop-blur-md border-b border-purple-900/30 transition-all duration-300">
      <div class="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
        <!-- Logo -->
        <Link href="/" class="flex items-center gap-3 group">
          <img src="/images/p1--000.png" alt="Premier One Logo" class="h-12 object-contain" />
        </Link>

        <!-- Navigation -->
        <div class="hidden md:flex items-center gap-8">
          <Link 
            v-for="nav in navigation" 
            :key="nav.id" 
            :href="nav.slug === 'home' ? '/' : `/${nav.slug}`"
            class="text-sm font-bold uppercase tracking-wider text-slate-400 hover:text-purple-400 transition-colors"
          >
            {{ nav.title }}
          </Link>
          
          <!-- Static links fallback -->
          <template v-if="!navigation.length">
            <a href="#about" class="text-sm font-bold uppercase tracking-wider text-slate-400 hover:text-purple-400 transition-colors">About Us</a>
            <a href="#activities" class="text-sm font-bold uppercase tracking-wider text-slate-400 hover:text-purple-400 transition-colors">Core Activities</a>
            <a href="#future" class="text-sm font-bold uppercase tracking-wider text-slate-400 hover:text-purple-400 transition-colors">Future</a>
            <a href="#contact" class="text-sm font-bold uppercase tracking-wider text-slate-400 hover:text-purple-400 transition-colors">Contact</a>
          </template>
        </div>

        <!-- Auth Actions -->
        <div class="flex items-center gap-4">
          <Link 
            v-if="user" 
            :href="route('admin.dashboard')" 
            class="inline-flex items-center justify-center px-4 py-2 bg-purple-600 hover:bg-purple-700 text-xs font-bold uppercase tracking-wider text-white rounded-none skew-x-[-10deg] shadow-lg shadow-purple-600/20 transition-all duration-200"
          >
            <span class="skew-x-[10deg] flex items-center">
              Dashboard
              <ArrowUpRight class="w-3.5 h-3.5 ml-1" />
            </span>
          </Link>
          <template v-else>
            <Link 
              :href="route('login')" 
              class="hidden sm:inline-flex items-center justify-center px-6 py-2 bg-purple-600 hover:bg-purple-700 text-xs font-bold uppercase tracking-wider text-white rounded-none skew-x-[-10deg] shadow-lg shadow-purple-600/20 transition-all duration-200"
            >
              <span class="skew-x-[10deg]">Sign In</span>
            </Link>
          </template>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <header class="relative max-w-7xl mx-auto px-6 pt-24 pb-32 md:pt-36 md:pb-48">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center relative z-10">
        <!-- Content -->
        <div class="space-y-8 text-left">
          <div class="inline-flex items-center gap-2 px-3 py-1 bg-purple-500/10 border border-purple-500/20 text-purple-400 text-xs font-bold uppercase tracking-widest skew-x-[-10deg]">
            <span class="skew-x-[10deg] flex items-center">
              <span class="w-1.5 h-1.5 bg-purple-400 rounded-full animate-pulse mr-2"></span>
              Experience the Rush of Motorsports
            </span>
          </div>

          <h1 class="text-5xl sm:text-6xl lg:text-7xl font-black tracking-tighter text-white uppercase leading-[1]">
            Start Your <br/>
            <span class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-indigo-600">
              Motorsports Dream
            </span>
          </h1>

          <p class="text-lg text-slate-400 font-medium max-w-xl">
            Premier One International Motorsport is a Malaysian-based development company focused on nurturing young racing talent through structured training and competitive exposure.
          </p>

          <!-- CTAs -->
          <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-4 pt-4">
            <a 
              href="#activities" 
              class="inline-flex items-center justify-center px-8 py-4 bg-purple-600 hover:bg-purple-700 text-sm font-bold uppercase tracking-wider text-white skew-x-[-10deg] hover:scale-[1.02] shadow-xl shadow-purple-600/30 transition-all duration-200"
            >
              <span class="skew-x-[10deg] flex items-center">
                Our Programs
                <ChevronRight class="w-4 h-4 ml-2" />
              </span>
            </a>
            <a 
              href="#contact" 
              class="inline-flex items-center justify-center px-8 py-4 bg-transparent border border-purple-500/30 hover:border-purple-500 hover:bg-purple-900/20 text-sm font-bold uppercase tracking-wider text-white skew-x-[-10deg] transition-all duration-200"
            >
              <span class="skew-x-[10deg] flex items-center">
                Contact Us
              </span>
            </a>
          </div>
        </div>

        <!-- Visual / Graphic -->
        <div class="relative flex justify-center lg:justify-end">
          <div class="relative w-full max-w-lg aspect-square">
            <div class="absolute inset-0 bg-gradient-to-tr from-purple-600 to-indigo-600 rounded-full blur-3xl opacity-20 animate-pulse"></div>
            <!-- Dynamic Hero Image from Extracted PDF (Grid Go Karts) -->
            <div class="w-full h-full skew-x-[-10deg] overflow-hidden border-4 border-purple-900/50 shadow-2xl relative z-10 bg-slate-900 flex items-center justify-center">
                <div class="skew-x-[10deg] w-[120%] h-full bg-[url('/images/p1--001.png')] bg-cover bg-center opacity-80 mix-blend-luminosity hover:mix-blend-normal transition-all duration-700"></div>
            </div>
            
            <!-- Floating Badge -->
            <div class="absolute -bottom-6 -left-6 bg-[#0a0510] border border-purple-500/30 p-4 skew-x-[-10deg] shadow-xl z-20 hidden md:block">
              <div class="skew-x-[10deg] flex items-center gap-4">
                <div class="w-12 h-12 bg-purple-600/20 flex items-center justify-center">
                  <Trophy class="w-6 h-6 text-purple-400" />
                </div>
                <div>
                  <h4 class="text-white font-black uppercase tracking-wider">Champion</h4>
                  <p class="text-xs text-slate-400">Winning Mindset</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- About Section -->
    <section id="about" class="py-24 bg-slate-950/50 relative border-y border-purple-900/20">
      <div class="max-w-7xl mx-auto px-6">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
          <div>
            <div class="w-full aspect-[4/3] skew-x-[-10deg] overflow-hidden border border-purple-900/50 relative">
               <div class="skew-x-[10deg] w-[120%] h-full ml-[-10%] bg-[url('/images/p1--002.png')] bg-cover bg-center opacity-70 mix-blend-luminosity hover:mix-blend-normal transition-all duration-700"></div>
            </div>
          </div>
          <div class="space-y-6 text-left">
            <span class="text-xs font-bold text-purple-400 uppercase tracking-widest">Introduction</span>
            <h2 class="text-4xl font-black text-white uppercase tracking-tighter">
              Developing Disciplined & Skilled Drivers
            </h2>
            <div class="w-20 h-1 bg-purple-600"></div>
            <p class="text-slate-400 leading-relaxed font-medium">
              Founded with a vision to bridge aspiring drivers from Malaysia and across the wider region with global motorsport opportunities, Premier One provides a platform for young talent to develop both on and off the track.
            </p>
            <p class="text-slate-400 leading-relaxed font-medium">
              We believe motorsport is not just about speed, but about discipline, consistency, and character. We aim to develop well-rounded individuals who can excel both in motorsport and in life.
            </p>
            <ul class="space-y-3 pt-4">
              <li class="flex items-center gap-3 text-slate-300 font-bold uppercase tracking-wide text-sm">
                <CheckCircle class="w-5 h-5 text-purple-500" /> Technical Driving Skills
              </li>
              <li class="flex items-center gap-3 text-slate-300 font-bold uppercase tracking-wide text-sm">
                <CheckCircle class="w-5 h-5 text-purple-500" /> Racecraft and Strategy
              </li>
              <li class="flex items-center gap-3 text-slate-300 font-bold uppercase tracking-wide text-sm">
                <CheckCircle class="w-5 h-5 text-purple-500" /> Mental Resilience
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Core Activities -->
    <section id="activities" class="py-24 relative">
      <div class="max-w-7xl mx-auto px-6">
        <div class="text-center max-w-3xl mx-auto space-y-4 mb-16">
          <span class="text-xs font-bold text-purple-400 uppercase tracking-widest">What We Do</span>
          <h2 class="text-4xl sm:text-5xl font-black text-white uppercase tracking-tighter">
            Core Activities
          </h2>
          <div class="w-20 h-1 bg-purple-600 mx-auto"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Card 1 -->
          <div class="group relative bg-[#0a0510] border border-purple-900/30 p-8 skew-x-[-5deg] hover:border-purple-500/50 transition-all duration-300">
            <div class="skew-x-[5deg] space-y-6">
              <h3 class="text-2xl font-black text-white uppercase tracking-tight group-hover:text-purple-400 transition-colors">
                Driver's Development
              </h3>
              <ul class="space-y-3 text-sm text-slate-400 font-medium">
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Karting training and coaching</li>
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Race preparation and performance analysis</li>
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Physical and mental conditioning</li>
              </ul>
            </div>
            <!-- Number watermark -->
            <div class="absolute -bottom-4 right-4 text-8xl font-black text-purple-900/20 z-0 select-none">01</div>
          </div>
          
          <!-- Card 2 -->
          <div class="group relative bg-[#0a0510] border border-purple-900/30 p-8 skew-x-[-5deg] hover:border-purple-500/50 transition-all duration-300 mt-0 md:mt-8">
            <div class="skew-x-[5deg] space-y-6">
              <h3 class="text-2xl font-black text-white uppercase tracking-tight group-hover:text-purple-400 transition-colors">
                Competitive Participation
              </h3>
              <ul class="space-y-3 text-sm text-slate-400 font-medium">
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Participation in local karting championships</li>
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Overseas championships</li>
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Exposure to multiple race formats</li>
              </ul>
            </div>
            <!-- Number watermark -->
            <div class="absolute -bottom-4 right-4 text-8xl font-black text-purple-900/20 z-0 select-none">02</div>
          </div>

          <!-- Card 3 -->
          <div class="group relative bg-[#0a0510] border border-purple-900/30 p-8 skew-x-[-5deg] hover:border-purple-500/50 transition-all duration-300 mt-0 md:mt-16">
            <div class="skew-x-[5deg] space-y-6">
              <h3 class="text-2xl font-black text-white uppercase tracking-tight group-hover:text-purple-400 transition-colors">
                International Pathway
              </h3>
              <ul class="space-y-3 text-sm text-slate-400 font-medium">
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Planned training in the UK</li>
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Support for drivers pursuing opportunities in the UK</li>
                <li class="flex items-start gap-2"><div class="w-1.5 h-1.5 bg-purple-500 mt-1.5 shrink-0"></div> Collaboration with UK-based circuits</li>
              </ul>
            </div>
            <!-- Number watermark -->
            <div class="absolute -bottom-4 right-4 text-8xl font-black text-purple-900/20 z-0 select-none">03</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Future Direction Section -->
    <section id="future" class="py-24 bg-slate-950/50 relative border-t border-purple-900/20">
      <div class="absolute inset-0 z-0">
        <div class="w-full h-full bg-[url('/images/p1--012.png')] bg-cover bg-center opacity-20 mix-blend-luminosity"></div>
        <div class="absolute inset-0 bg-gradient-to-t from-[#0a0510] via-[#0a0510]/80 to-[#0a0510]"></div>
      </div>
      
      <div class="max-w-7xl mx-auto px-6 relative z-10">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
          <div class="space-y-6 text-left">
            <span class="text-xs font-bold text-purple-400 uppercase tracking-widest">Future Direction</span>
            <h2 class="text-4xl sm:text-5xl font-black text-white uppercase tracking-tighter">
              International <br/>Expansion
            </h2>
            <div class="w-20 h-1 bg-purple-600"></div>
            <p class="text-slate-300 leading-relaxed font-medium">
              Premier One is currently developing an international expansion strategy, including the establishment of a UK-based platform to support driver progression into the British karting scene.
            </p>
            <p class="text-slate-300 leading-relaxed font-medium">
              This initiative aims to create a structured bridge between Malaysian drivers including in the wider region and the UK motorsport ecosystem.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer / Contact -->
    <footer id="contact" class="border-t border-purple-900/30 bg-[#06030a] py-16 text-slate-400 relative z-10">
      <div class="max-w-7xl mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-12 gap-12 text-left mb-12">
          
          <div class="md:col-span-5 space-y-6">
            <div class="font-black text-2xl tracking-tighter text-white italic flex items-center">
              <img src="/images/p1--000.png" alt="Premier One Logo" class="h-10 object-contain" />
            </div>
            <p class="text-sm text-slate-400 leading-relaxed max-w-sm">
              Safety is a top priority in all our activities. All training sessions are conducted in controlled environments and supervised by experienced personnel.
            </p>
          </div>

          <div class="md:col-span-4 space-y-4">
            <h4 class="text-xs font-bold text-white uppercase tracking-widest">Headquarters</h4>
            <ul class="space-y-3 text-sm">
              <li class="flex items-start gap-2">
                <MapPin class="w-4 h-4 text-purple-400 shrink-0 mt-0.5" />
                <span>No. 4, Jalan Kristal 7/67A, Seksyen 7<br/>40000 Shah Alam, Selangor Darul Ehsan</span>
              </li>
              <li class="flex items-start gap-2 mt-2">
                <span class="text-purple-500 font-bold shrink-0 mt-0.5">Branch Offices:</span>
                <span>Selangor, Penang, Johor</span>
              </li>
            </ul>
          </div>

          <div class="md:col-span-3 space-y-4">
            <h4 class="text-xs font-bold text-white uppercase tracking-widest">Contact Us</h4>
            <ul class="space-y-3 text-sm">
              <li class="flex items-center gap-2">
                <Mail class="w-4 h-4 text-purple-400" />
                <a href="mailto:premier1msport@gmail.com" class="hover:text-purple-400 transition-colors">premier1msport@gmail.com</a>
              </li>
            </ul>
          </div>
        </div>

        <div class="pt-8 border-t border-purple-900/20 flex flex-col sm:flex-row items-center justify-between gap-4">
          <p class="text-xs font-semibold uppercase tracking-wider">
            &copy; {{ new Date().getFullYear() }} Premier One International Motorsport Sdn Bhd. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>
