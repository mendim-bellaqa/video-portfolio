<template>
  <div class="bg-black text-gray-100 min-h-screen font-sans antialiased overflow-x-hidden">
    <!-- Header -->
    <header
      :class="['fixed top-0 left-0 right-0 z-50 transition-all duration-300 ease-in-out',
               scrolled || isMenuOpen ? 'bg-black py-4 shadow-lg' : 'bg-transparent py-6']">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between">
          <div class="flex-shrink-0">
            <a href="#hero" class="text-3xl font-extrabold text-white hover:text-amber-400 transition duration-300 tracking-tight">
              MENDIM BELLAQA
            </a>
          </div>
          <div class="hidden md:block">
            <nav class="ml-10 flex items-center space-x-6">
              <a v-for="link in navLinks" :key="link.text" :href="link.href"
                 class="px-3 py-2 rounded-md text-sm font-medium text-gray-300 hover:text-amber-400 transition duration-300 uppercase tracking-wider relative group">
                {{ link.text }}
                <span class="absolute bottom-0 left-0 w-full h-0.5 bg-amber-400 transform scale-x-0 group-hover:scale-x-100 transition-transform duration-300 ease-out"></span>
              </a>
            </nav>
          </div>
          <div class="hidden md:block ml-6">
            <a href="#contact"
               class="inline-flex items-center px-6 py-2 border-2 border-amber-400 text-sm font-medium rounded-sm text-amber-400 hover:bg-white hover:text-black transition duration-300 uppercase tracking-wider">
              Get a Quote
            </a>
          </div>
          <div class="-mr-2 flex md:hidden">
            <button @click="toggleMenu" type="button"
                    class="text-gray-300 hover:text-amber-400 inline-flex items-center justify-center p-2 rounded-md focus:outline-none"
                    aria-controls="mobile-menu" aria-expanded="false">
              <span class="sr-only">Open main menu</span>
              <i :class="isMenuOpen ? 'fas fa-times' : 'fas fa-bars'" class="h-6 w-6"></i>
            </button>
          </div>
        </div>
      </div>

      <!-- Mobile menu -->
      <transition
        enter-active-class="transition ease-out duration-200 transform"
        enter-from-class="opacity-0 scale-95"
        enter-to-class="opacity-100 scale-100"
        leave-active-class="transition ease-in duration-150 transform"
        leave-from-class="opacity-100 scale-100"
        leave-to-class="opacity-0 scale-95"
      >
        <div v-if="isMenuOpen" class="md:hidden absolute top-full left-0 right-0 bg-black shadow-xl" id="mobile-menu">
          <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
            <a v-for="link in navLinks" :key="link.text" :href="link.href" @click="isMenuOpen = false"
               class="block px-3 py-3 rounded-md text-base font-medium text-gray-200 hover:text-amber-400 hover:bg-gray-800 transition duration-300 uppercase tracking-wider text-center">
              {{ link.text }}
            </a>
          </div>
          <div class="pt-4 pb-4 border-t border-gray-700">
            <div class="flex items-center justify-center px-5">
               <a href="#contact" @click="isMenuOpen = false"
                 class="w-full inline-flex items-center justify-center px-6 py-3 border-2 border-amber-400 text-sm font-medium rounded-sm text-amber-400 hover:bg-amber-400 hover:text-black transition duration-300 uppercase tracking-wider">
                Get a Quote
              </a>
            </div>
          </div>
        </div>
      </transition>
    </header>


    
    <!-- Hero Section -->
    <section
      id="hero"
      class="min-h-screen flex items-center justify-center relative text-white text-center p-4 overflow-hidden bg-black"
    >
      <!-- Video Background -->
      <video
        ref="heroVideoPlayer"
        :src="heroVideoPath"
        :poster="heroBackgroundImage"
        autoplay
        loop
        muted
        playsinline
        class="absolute inset-0 w-full h-full object-cover z-0"
        @play="isHeroVideoPlaying = true"
        @pause="isHeroVideoPlaying = false"
        @volumechange="onHeroVideoVolumeChange"
      ></video>

      <!-- Dark Overlay for text readability -->
      <div class="absolute inset-0 bg-black opacity-50 z-10"></div>

      <!-- Content -->
      <div class="relative z-20 animate-fadeInUp">
        <h2 class="text-xl sm:text-2xl text-amber-400 font-medium mb-4 uppercase tracking-widest">
          Video Editing & Motion Design
        </h2>
        <h1 class="text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-extrabold leading-tight mb-6 tracking-tighter">
          MENDIM BELLAQA
        </h1>
        <p class="text-lg sm:text-xl text-gray-200 max-w-3xl mx-auto leading-relaxed mb-8" ref="tagline">
          {{ animatedTagline }}
        </p>

        <div class="flex flex-col sm:flex-row items-center justify-center gap-4 sm:gap-6">
          <a href="#about-me" 
             class="text-3xl text-gray-400 hover:text-amber-400 transition animate-bounce 
                    mb-4 sm:mb-0">
            <i class="fas fa-chevron-down"></i>
          </a>
          <a href="#featured-projects"
             class="inline-block bg-amber-400 hover:bg-amber-500 text-black font-bold py-4 px-10 rounded-sm text-lg sm:text-xl transition duration-300 ease-in-out transform hover:scale-105 shadow-xl">
            View My Work
          </a>
          <a href="#contact"
             class="inline-block bg-transparent hover:bg-white text-white font-semibold hover:text-black py-4 px-10 border-2 border-white rounded-sm text-lg sm:text-xl transition duration-300 ease-in-out shadow-lg">
            Contact Me
          </a>
        </div>
      </div>
    </section>
    <!-- Portfolio Section -->
    <section id="featured-projects" class="py-20 md:py-32 bg-black">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16 md:mb-20">
          <h2 class="text-sm text-amber-400 uppercase tracking-widest font-semibold mb-3">My Work</h2>
          <h3 class="text-4xl md:text-5xl font-extrabold text-white tracking-tight">Featured Projects</h3>
          <p class="text-gray-400 max-w-2xl mx-auto mt-4">A selection of my best work across different genres and styles</p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2 gap-4 md:gap-6">
          <div v-for="(video, index) in featuredVideos" :key="video.id"
               class="group relative aspect-w-16 aspect-h-9 rounded-md overflow-hidden cursor-pointer shadow-lg animate-on-scroll"
               data-animation="zoomIn" :style="{transitionDelay: `${index * 100}ms`}"
               @click="openProjectModal(video)">
            <img :src="getImagePath(video.thumbnail)" :alt="video.title"
                 class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-500 ease-in-out">
            <div class="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent opacity-70 group-hover:opacity-50 transition-opacity duration-300"></div>
            <div class="absolute inset-0 flex flex-col items-center justify-center p-6 text-center opacity-0 group-hover:opacity-100 transition-all duration-300 transform group-hover:translate-y-0 translate-y-8">
              <h4 class="text-xl lg:text-2xl font-bold text-white mb-1">{{ video.title }}</h4>
              <p class="text-xs text-amber-300 uppercase tracking-wider">{{ video.category }}</p>
              <span class="mt-4 p-3 bg-amber-400 text-black rounded-full text-lg">
                <i class="fas fa-play"></i>
              </span>
            </div>
          </div>
        </div>

        <div class="text-center mt-16">
          <a href="#" class="text-amber-400 border border-amber-400 hover:bg-amber-400 hover:text-black font-semibold py-3 px-8 rounded-sm uppercase tracking-wider transition duration-300 inline-flex items-center">
            View All Projects <i class="fas fa-arrow-right ml-2"></i>
          </a>
        </div>
      </div>
    </section>

    <!-- About Me Section -->
    <section id="about-me" class="py-20 md:py-32 bg-black">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="lg:grid lg:grid-cols-2 lg:gap-16 lg:items-center">
          <div class="mb-12 lg:mb-0">
            <h2 class="text-sm text-amber-400 uppercase tracking-widest font-semibold mb-3">Who I Am</h2>
            <h3 class="text-4xl md:text-5xl font-extrabold text-white mb-6 tracking-tight">
              Creative Vision, <span class="block">Technical Precision.</span>
            </h3>
            <p class="text-gray-400 text-lg leading-relaxed mb-6">
              Mendim Bellaqa, an Albanian visual artist from Kosovo, born in Vaduz, Liechtenstein. My passion lies in transforming raw footage into compelling, emotional narratives that captivate and inspire.
            </p>
            <p class="text-gray-400 text-lg leading-relaxed mb-8">
              With over <strong class="text-amber-400">{{ animatedStats.projects }}+</strong> projects delivered and a <strong class="text-amber-400">{{ animatedStats.satisfaction }}%</strong> client satisfaction rate, I am dedicated to exceeding expectations and crafting unforgettable cinematic experiences.
            </p>
            <div class="flex flex-wrap gap-4">
              <a href="#contact" class="inline-block bg-amber-400 text-black font-bold py-3 px-8 rounded-sm text-md uppercase tracking-wider hover:bg-amber-500 transition duration-300">
                Let's Talk
              </a>
              <a href="#skills" class="inline-block bg-transparent border border-amber-400 text-amber-400 font-bold py-3 px-8 rounded-sm text-md uppercase tracking-wider hover:bg-amber-400 hover:text-black transition duration-300">
                My Services
              </a>
            </div>
          </div>

          <div class="relative animate-on-scroll" data-animation="slideInRight">
            <!-- Background Light Boxes -->
            <div class="absolute -inset-4 sm:-inset-6 md:-inset-8 opacity-10 sm:opacity-15 z-0 pointer-events-none">
              <div class="absolute top-1/4 left-0 w-1/2 h-1/3 bg-amber-400 rounded-lg blur-3xl animate-pulse-slow-1"></div>
              <div class="absolute bottom-0 right-0 w-1/3 h-1/2 bg-blue-500 rounded-lg blur-3xl animate-pulse-slow-2 opacity-70"></div>
              <div class="absolute top-0 right-1/4 w-1/2 h-1/2 bg-purple-500 rounded-lg blur-3xl animate-pulse-slow-3 opacity-60"></div>
            </div>

            <!-- Image Container -->
            <div class="relative p-2 sm:p-3 z-10">
               <div class="absolute z-0 -inset-3 sm:-inset-4 md:-inset-5 border-2 sm:border-3 border-white left-5 rounded-lg opacity-100"></div>
              <div class="absolute z-0 -top-1 -left-1 sm:-top-2 sm:-left-2 md:-top-3 md:-left-3 w-full h-full border-2 sm:border-3 border-white rounded-lg opacity-70"></div>
              <div class="absolute z-0 -bottom-1 -right-1 sm:-bottom-2 sm:-right-2 md:-bottom-3 md:-right-3 w-full h-full border-2 sm:border-3 border-white rounded-lg opacity-50"></div>
           
              <img :src="getImagePath('profile.jpg')" alt="Mendim Bellaqa - Video Editor"
                  class="relative z-10 rounded-lg shadow-2xl w-full h-auto object-cover">
              </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section id="skills" class="py-20 md:py-32 bg-gray-900">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16 md:mb-20">
          <h2 class="text-sm text-amber-400 uppercase tracking-widest font-semibold mb-3">What I Offer</h2>
          <h3 class="text-4xl md:text-5xl font-extrabold text-white tracking-tight">My Services</h3>
          <p class="text-gray-400 max-w-2xl mx-auto mt-4">Comprehensive video production services tailored to your creative needs</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 md:gap-12">
          <div v-for="(skill, index) in skills" :key="skill.name"
               class="bg-black p-8 rounded-lg shadow-2xl border border-gray-800 hover:border-amber-400 transition-all duration-300 transform hover:-translate-y-2 animate-on-scroll"
               :data-animation="index % 3 === 0 ? 'slideInLeft' : (index % 3 === 1 ? 'fadeInUp' : 'slideInRight')" :style="{transitionDelay: `${index * 100}ms`}">
            <div class="text-4xl text-amber-400 mb-6"><i :class="skill.icon"></i></div>
            <h4 class="text-2xl font-bold text-white mb-3">{{ skill.name }}</h4>
            <p class="text-gray-400 leading-relaxed mb-4">{{ skill.description }}</p>
            <ul class="text-gray-400 text-sm space-y-2">
              <li v-for="item in skill.items" :key="item" class="flex items-start">
                <i class="fas fa-check text-amber-400 mt-1 mr-2 text-xs"></i>
                <span>{{ item }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20 md:py-32 bg-gray-900 relative overflow-hidden">
      <div class="absolute inset-0 opacity-10 z-0 pattern-bg"></div>

      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="lg:grid lg:grid-cols-2 lg:gap-16">
          <div class="mb-12 lg:mb-0 animate-on-scroll" data-animation="slideInLeft">
            <h2 class="text-sm text-amber-400 uppercase tracking-widest font-semibold mb-3">Get In Touch</h2>
            <h3 class="text-4xl md:text-5xl font-extrabold text-white mb-6 tracking-tight">Let's Work Together</h3>
            <p class="text-gray-400 text-lg leading-relaxed mb-8">
              Have a project in mind? Want to discuss potential collaboration? Feel free to reach out through any of the channels below.
            </p>

            <div class="space-y-6">
              <div class="flex items-start">
                <div class="text-amber-400 text-xl mr-4 mt-1">
                  <i class="fas fa-envelope"></i>
                </div>
                <div>
                  <h4 class="text-lg font-bold text-white mb-1">Email Me</h4>
                  <a href="mailto:bellaqamendim@gmail.com" class="text-gray-400 hover:text-amber-400 transition duration-300">bellaqamendim@gmail.com</a>
                </div>
              </div>

              <div class="flex items-start">
                <div class="text-amber-400 text-xl mr-4 mt-1">
                  <i class="fas fa-phone-alt"></i>
                </div>
                <div>
                  <h4 class="text-lg font-bold text-white mb-1">Call Me</h4>
                  <a href="tel:+38349240035" class="text-gray-400 hover:text-amber-400 transition duration-300">+383 49 240 035</a>
                </div>
              </div>

              <div class="flex items-start">
                <div class="text-amber-400 text-xl mr-4 mt-1">
                  <i class="fas fa-map-marker-alt"></i>
                </div>
                <div>
                  <h4 class="text-lg font-bold text-white mb-1">Location</h4>
                  <p class="text-gray-400"> Kosovo</p>
                </div>
              </div>
            </div>

            <div class="mt-10 flex space-x-4">
              <a href="https://www.linkedin.com/in/mendimbellaqa/" target="_blank" class="text-gray-400 hover:text-amber-400 text-2xl transition duration-300">
                <i class="fab fa-linkedin"></i>
              </a>
              <a href="#" target="_blank" class="text-gray-400 hover:text-red-500 text-2xl transition duration-300">
                <i class="fab fa-youtube"></i>
              </a>
              <a href="#" class="text-gray-400 hover:text-blue-400 text-2xl transition duration-300">
                <i class="fab fa-vimeo-v"></i>
              </a>
            </div>
          </div>

          <div class="animate-on-scroll" data-animation="slideInRight">
            <div class="bg-black p-8 rounded-lg shadow-2xl border border-gray-800">
              <h4 class="text-2xl font-bold text-white mb-6">Send Me a Message</h4>
              <form @submit.prevent="submitForm" class="space-y-6">
                <div>
                  <label for="name" class="block text-sm font-medium text-gray-400 mb-1">Your Name</label>
                  <input type="text" id="name" v-model="form.name" required
                         class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-sm focus:outline-none focus:ring-2 focus:ring-amber-400 focus:border-transparent text-white">
                </div>

                <div>
                  <label for="email" class="block text-sm font-medium text-gray-400 mb-1">Your Email</label>
                  <input type="email" id="email" v-model="form.email" required
                         class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-sm focus:outline-none focus:ring-2 focus:ring-amber-400 focus:border-transparent text-white">
                </div>

                <div>
                  <label for="subject" class="block text-sm font-medium text-gray-400 mb-1">Subject</label>
                  <input type="text" id="subject" v-model="form.subject" required
                         class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-sm focus:outline-none focus:ring-2 focus:ring-amber-400 focus:border-transparent text-white">
                </div>

                <div>
                  <label for="message" class="block text-sm font-medium text-gray-400 mb-1">Your Message</label>
                  <textarea id="message" v-model="form.message" rows="5" required
                            class="w-full px-4 py-3 bg-gray-800 border border-gray-700 rounded-sm focus:outline-none focus:ring-2 focus:ring-amber-400 focus:border-transparent text-white"></textarea>
                </div>

                <button type="submit" class="w-full bg-amber-400 hover:bg-amber-500 text-white font-bold py-4 px-6 rounded-sm uppercase tracking-wider transition duration-300">
                  <span v-if="!form.submitting">Send Message</span>
                  <span v-else class="flex items-center justify-center">
                    <i class="fas fa-spinner fa-spin mr-2"></i> Sending...
                  </span>
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-black border-t border-gray-800 py-10">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-6 md:mb-0">
            <a href="#hero" class="text-2xl font-extrabold text-white hover:text-amber-400 transition duration-300">
              MENDIM BELLAQA
            </a>
          </div>

          <div class="flex flex-col items-center md:items-end">
            <p class="text-gray-600 text-sm mb-2">
              © {{ new Date().getFullYear() }} MENDIM BELLAQA. All Rights Reserved.
            </p>
            <p class="text-xs text-gray-700">
              Crafted with <i class="fas fa-heart text-amber-400"></i> in Kosovo.
            </p>
          </div>
        </div>
      </div>
    </footer>

    <!-- Project Modal -->
    <div v-if="currentModalVideo"
         class="fixed inset-0 bg-black bg-opacity-90 z-[60]  mt-20 flex items-center justify-center p-4"
         @click.self="closeProjectModal">
      <div class="bg-gray-900 p-2 sm:p-4 rounded-lg shadow-xl max-w-3xl w-full relative animate-zoomIn">
        <button @click="closeProjectModal" class="absolute -top-3 -right-3 sm:top-2 sm:right-2 text-white bg-amber-500 hover:bg-amber-600 rounded-full p-2 text-xl leading-none z-10">
          <i class="fas fa-times"></i>
        </button>
        <div class="aspect-w-16 aspect-h-9">
          <iframe v-if="isEmbedLink(currentModalVideo.reelLink)"
                  :src="getEmbedUrl(currentModalVideo.reelLink)"
                  frameborder="0"
                  allow="autoplay; fullscreen; picture-in-picture"
                  allowfullscreen
                  class="w-full h-full"></iframe>
          <video v-else-if="currentModalVideo.videoFile"
                 :src="getVideoPath(currentModalVideo.videoFile)"
                 controls autoplay class="w-full h-full object-contain"></video>
          <div v-else class="w-full h-full flex items-center justify-center bg-black text-gray-400">
            Video preview not available.
          </div>
        </div>
        <div class="p-4 text-center">
          <h3 class="text-2xl font-bold text-white mt-2">{{ currentModalVideo.title }}</h3>
          <p class="text-amber-400 uppercase text-sm mb-4">{{ currentModalVideo.category }}</p>
          <p class="text-gray-400">{{ currentModalVideo.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      heroBackgroundImage: '/assets/images/video-editing-background.png',
      heroVideoPath: '/assets/videos/hero-grapes-video.mp4',
      isHeroVideoPlaying: false,
      isHeroVideoMuted: true,
      heroVideoVolume: 0,
      heroVideoPlayer: null,

      isMenuOpen: false,
      scrolled: false,
      vineVideoPath: '/assets/videos/vine.mp4',
      danceVideoPath: '/assets/videos/dance-with-me.mp4',

      // Video player data
      videoPlayer: null,
      videoPlayerContainer: null,
      isPlaying: false,
      isMuted: true,
      volume: 0,
      progress: 0,
      buffered: 0,
      currentTime: 0,
      duration: 0,
      isFullscreen: false,
      isMobileControlsHidden: true,

      // Dance video player data
      danceVideoPlayer: null,
      danceVideoContainer: null,
      isDancePlaying: false,
      isDanceMuted: true,
      danceVolume: 0,
      danceProgress: 0,
      danceBuffered: 0,
      danceCurrentTime: 0,
      danceDuration: 0,
      isDanceFullscreen: false,
      
      navLinks: [
        { text: 'Home', href: '#hero' },
        { text: 'About', href: '#about-me' },
        { text: 'Services', href: '#skills' },
        { text: 'Portfolio', href: '#featured-projects' },
        { text: 'YouTube', href: '#youtube' },
        { text: 'Contact', href: '#contact' },
      ],
      fullTagline: "We don't just edit videos; we craft cinematic experiences. Frame by frame, pixel by pixel, turning your vision into a visual masterpiece.",
      animatedTagline: "",
      featuredVideos: [
        {
            id: 4,
            title: '',
            category: 'Motion Graphics',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'TEXT TRANSITION.mp4',
            description: 'Dynamic Motion Graphics'
        },
        {
            id: 5,
            title: 'ICE',
            category: 'Ad',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'ice-ads.mp4',
            description: 'A visually stunning short film titled "ICE".'
        },
        {
            id: 5,
            title: 'After Effect Intro TV SHow / Tradition / Village / Nature',
            category: 'Tradition / Village / Nature',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'sample-video.mp4',
            description: 'A high-energy commercial project showcasing innovative editing techniques and dynamic motion graphics.'
        },
        {
            id: 6,
            title: 'Culture Intro TV SHOW After Effect',
            category: 'Culture',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'sample-video-3.mp4',
            description: 'Corporate brand story that combines interview footage with b-roll to create a compelling narrative.'
        },
        {
            id: 3,
            title: 'After Effect Intro Documentary',
            category: 'Documentary',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'sample-video-2.mp4',
            description: 'Intro Documentary video featuring creative classic design / war topic'
        },
        {
            id: 4,
            title: 'Long Video / Generated / Music made by Me / Effects / Zoom',
            category: 'Narrative',
             thumbnail: 'main-thumb.jpeg',
            reelLink: 'https://www.youtube.com/watch?v=sWgksfT-9Go&t=210s',
            description: 'Short film with dramatic pacing, emotional storytelling, and cinematic color grading.'
        },
        {
            id: 0,
            title: 'Dance With ME USA',
            category: 'Dance Video AD',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'dance-with-me.mp4',
            description: ' A vibrant dance video showcasing the energy and passion of dance, set to an upbeat soundtrack.'
        },
        {
            id: 8,
            title: 'ST LIDERSHIP',
            category: 'Training Online Course',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'lidership.mp4',
            description: ' An online course video designed to educate and inspire viewers on leadership principles and practices.'
        },
        {
            id: 9,
            title: 'Short/REEL',
            category: 'Motion Video Edit',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'sample5.mp4',
            description: ' A collection of short, engaging videos designed for quick consumption and entertainment.'
        },
        {
            id: 10,
            title: 'Short/REEL',
            category: '',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'sample6.mp4',
            description: 'Tiktok Edit - A collection of short, engaging videos designed for quick consumption and entertainment.'
        },
        {
            id: 11,
            title: 'HAcker',
            category: 'Storytelling',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'sample7.mp4',
            description: 'Storytelling video with a focus on trensitions, icons, sound.'
        },
        {
            id: 1,
            title: '',
            category: '',
            thumbnail: 'main-thumb.jpeg',
            videoFile: 'vine.mp4',
            description: 'Vine Video Showcase - A collection of short, engaging videos designed for quick consumption and entertainment.'
        },
      ],
      skills: [
        {
            name: 'Film & Video Editing',
            icon: 'fas fa-film',
            description: 'Seamless editing for narrative films, commercials, corporate videos, and social media content.',
            items: [
                'Adobe Premiere Pro',
                'Adobe Photoshop',
                'Wondershare Filmora',
                'Storytelling & Pacing',
                'Multi-cam Editing'
            ]
        },
        {
            name: 'Motion Graphics Design',
            icon: 'fas fa-project-diagram',
            description: 'Creating captivating motion titles, lower thirds, infographics, and VFX to elevate your story.',
            items: [
                'Adobe After Effects',
                'Cinema 4D',
                '2D & 3D Animation',
                'Motion Tracking',
                'Visual Effects'
            ]
        },
        {
            name: 'Color Correction & Grading',
            icon: 'fas fa-palette',
            description: 'Expert color balancing, grading, and look development to achieve the perfect cinematic aesthetic.',
            items: [
                'DaVinci Resolve',
                'Color Theory',
                'Look Development',
                'Skin Tone Correction',
                'HDR Grading'
            ]

            
        },

                { name: 'Sound Design & Mixing', icon: 'fas fa-volume-up', description: 'Crafting immersive soundscapes, dialogue editing, and final mixing for impactful audio.', items: ['Adobe Audition', 'Sound Effects', 'Dialogue Cleanup', 'Audio Mixing', 'Foley Recording'] },

      ],
      stats: { projects: 500, satisfaction: 98 },
      animatedStats: { projects: 0, satisfaction: 0 },
      currentModalVideo: null,
      observer: null,
      form: {
        name: '',
        email: '',
        subject: '',
        message: '',
        submitting: false
      }
    };
  },
  mounted() {
    // Setup for custom video players
    this.$nextTick(() => {
      // Hero Video Player Setup
      if (this.$refs.heroVideoPlayer) {
        this.heroVideoPlayer = this.$refs.heroVideoPlayer;
        this.isHeroVideoMuted = this.heroVideoPlayer.muted;
        this.heroVideoVolume = this.heroVideoPlayer.muted ? 0 : this.heroVideoPlayer.volume;
        
        this.heroVideoPlayer.play()
          .then(() => {
            this.isHeroVideoPlaying = !this.heroVideoPlayer.paused;
          })
          .catch(error => {
            console.info("Autoplay for hero video may require user interaction or was prevented:", error.message);
            this.isHeroVideoPlaying = false;
          });
        this.onHeroVideoVolumeChange(); // Initialize volume state display
      }

      // Vine Video Player Setup
      if (this.$refs.videoPlayer && this.$refs.videoPlayerContainer) {
        this.videoPlayer = this.$refs.videoPlayer;
        this.videoPlayerContainer = this.$refs.videoPlayerContainer;
        
        this.isMuted = this.videoPlayer.muted;
        this.volume = this.videoPlayer.muted ? 0 : this.videoPlayer.volume;

        this.videoPlayer.play().catch(error => {
          console.info("Autoplay was prevented for vine video:", error.message);
          this.isPlaying = false;
        }).then(() => {
            if(this.videoPlayer) this.isPlaying = !this.videoPlayer.paused;
        });

        window.addEventListener('keydown', this.handleKeyboardControls);
        document.addEventListener('fullscreenchange', this.handleFullscreenChange);
        document.addEventListener('webkitfullscreenchange', this.handleFullscreenChange);
        document.addEventListener('mozfullscreenchange', this.handleFullscreenChange);
        document.addEventListener('MSFullscreenChange', this.handleFullscreenChange);

        this.videoPlayer.addEventListener('progress', this.updateBuffer);
      }

      // Dance Video Player Setup
      if (this.$refs.danceVideoPlayer && this.$refs.danceVideoContainer) {
        this.danceVideoPlayer = this.$refs.danceVideoPlayer;
        this.danceVideoContainer = this.$refs.danceVideoContainer;
        
        this.isDanceMuted = this.danceVideoPlayer.muted;
        this.danceVolume = this.danceVideoPlayer.muted ? 0 : this.danceVideoPlayer.volume;

        this.danceVideoPlayer.addEventListener('progress', this.updateDanceBuffer);
      }
    });
    
    this.typeTagline();
    this.animateAllStats();
    window.addEventListener('scroll', this.handleScroll);
    this.initScrollAnimations();
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
    if (this.observer) {
      this.observer.disconnect();
    }

    window.removeEventListener('keydown', this.handleKeyboardControls);
    document.removeEventListener('fullscreenchange', this.handleFullscreenChange);
    document.removeEventListener('webkitfullscreenchange', this.handleFullscreenChange);
    document.removeEventListener('mozfullscreenchange', this.handleFullscreenChange);
    document.removeEventListener('MSFullscreenChange', this.handleFullscreenChange);
    
    if (this.videoPlayer) {
      this.videoPlayer.removeEventListener('progress', this.updateBuffer);
    }
    
    if (this.danceVideoPlayer) {
      this.danceVideoPlayer.removeEventListener('progress', this.updateDanceBuffer);
    }
  },
  methods: {
    getImagePath(filename) {
      return `/assets/images/${filename}`;
    },
    getVideoPath(filename) {
      return `/assets/videos/${filename}`;
    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
      if (this.isMenuOpen) {
        document.body.style.overflow = 'hidden';
      } else {
        document.body.style.overflow = '';
      }
    },
    handleScroll() {
      this.scrolled = window.scrollY > 50;
    },
    typeTagline() {
      let i = 0;
      const speed = 30;
      const type = () => {
        if (i < this.fullTagline.length) {
          this.animatedTagline += this.fullTagline.charAt(i);
          i++;
          setTimeout(type, speed);
        }
      };
      this.$nextTick(() => {
        if (this.$refs.tagline) type();
      });
    },
    animateStat(key, endValue, duration = 2000) {
      let startTimestamp = null;
      const step = (timestamp) => {
        if (!startTimestamp) startTimestamp = timestamp;
        const progress = Math.min((timestamp - startTimestamp) / duration, 1);
        this.animatedStats[key] = Math.floor(progress * endValue);
        if (progress < 1) window.requestAnimationFrame(step);
        else this.animatedStats[key] = endValue;
      };
      window.requestAnimationFrame(step);
    },
    animateAllStats() {
      this.animateStat('projects', this.stats.projects);
      this.animateStat('satisfaction', this.stats.satisfaction);
    },
    openProjectModal(video) {
      this.currentModalVideo = video;
      document.body.style.overflow = 'hidden';
    },
    closeProjectModal() {
      this.currentModalVideo = null;
      document.body.style.overflow = '';
    },
    isEmbedLink(url) {
      return url && (url.includes('youtube.com') || url.includes('youtu.be') || url.includes('vimeo.com'));
    },
    getEmbedUrl(url) {
      if (!url) return '';
      if (url.includes('youtube.com/watch?v=')) {
        const videoId = url.split('v=')[1].split('&')[0];
        return `https://www.youtube.com/embed/${videoId}?autoplay=1&rel=0`;
      }
      if (url.includes('youtu.be/')) {
        const videoId = url.split('youtu.be/')[1].split('?')[0];
        return `https://www.youtube.com/embed/${videoId}?autoplay=1&rel=0`;
      }
      if (url.includes('vimeo.com/')) {
        const videoId = url.split('vimeo.com/')[1].split('?')[0];
        return `https://player.vimeo.com/video/${videoId}?autoplay=1&title=0&byline=0&portrait=0`;
      }
      return url;
    },
    initScrollAnimations() {
      this.observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const animationType = entry.target.dataset.animation || 'fadeInUp';
            entry.target.classList.add(animationType);
            entry.target.classList.add('in-view');
          }
        });
      }, { threshold: 0.1 });

      document.querySelectorAll('.animate-on-scroll').forEach(el => {
        this.observer.observe(el);
      });
    },
    submitForm() {
      this.form.submitting = true;
      setTimeout(() => {
        alert('Thank you for your message! I will get back to you soon.');
        this.form = {
          name: '',
          email: '',
          subject: '',
          message: '',
          submitting: false
        };
      }, 1500);
    },
    
    // Hero Video Control Methods
    toggleHeroPlay() {
      if (!this.heroVideoPlayer) return;
      if (this.heroVideoPlayer.paused || this.heroVideoPlayer.ended) {
        this.heroVideoPlayer.play().catch(e => console.error("Error playing hero video:", e));
      } else {
        this.heroVideoPlayer.pause();
      }
    },
    toggleHeroMute() {
      if (!this.heroVideoPlayer) return;
      this.heroVideoPlayer.muted = !this.heroVideoPlayer.muted;
      if (!this.heroVideoPlayer.muted && this.heroVideoPlayer.volume === 0) {
          this.heroVideoPlayer.volume = 0.5;
      }
    },
    handleHeroVolumeChange(event) {
      if (!this.heroVideoPlayer) return;
      const newVolume = parseFloat(event.target.value);
      this.heroVideoPlayer.volume = newVolume;
      this.heroVideoPlayer.muted = newVolume === 0;
    },
    onHeroVideoVolumeChange() {
      if (!this.heroVideoPlayer) return;
      this.isHeroVideoMuted = this.heroVideoPlayer.muted || this.heroVideoPlayer.volume === 0;
      this.heroVideoVolume = this.heroVideoPlayer.volume;
    },

    // Vine Video Player Methods
    handleVideoMetadata() {
      if (!this.videoPlayer) return;
      this.duration = this.videoPlayer.duration;
      this.updateBuffer();
    },
    togglePlay() {
      if (!this.videoPlayer) return;
      if (this.videoPlayer.paused || this.videoPlayer.ended) {
        this.videoPlayer.play().catch(e => console.error("Error playing video:", e));
      } else {
        this.videoPlayer.pause();
      }
    },
    updateProgress() {
      if (!this.videoPlayer) return;
      this.currentTime = this.videoPlayer.currentTime;
      if (this.duration > 0) {
        this.progress = (this.videoPlayer.currentTime / this.duration) * 100;
      } else {
        this.progress = 0;
      }
    },
    updateBuffer() {
        if (!this.videoPlayer || !this.videoPlayer.buffered || this.videoPlayer.buffered.length === 0 || this.duration === 0) {
            this.buffered = 0;
            return;
        }
        let bufferedEnd = 0;
        for (let i = 0; i < this.videoPlayer.buffered.length; i++) {
            if (this.videoPlayer.buffered.start(i) <= this.videoPlayer.currentTime && this.videoPlayer.buffered.end(i) >= this.videoPlayer.currentTime) {
                 bufferedEnd = this.videoPlayer.buffered.end(i);
                 break;
            }
            if (this.videoPlayer.buffered.length > 0 && (i === this.videoPlayer.buffered.length -1 || bufferedEnd === 0) ) {
                bufferedEnd = this.videoPlayer.buffered.end(this.videoPlayer.buffered.length - 1);
            }
        }
        this.buffered = (bufferedEnd / this.duration) * 100;
    },
    seekVideo(event) {
        if (!this.videoPlayer || this.duration === 0) return;
        const progressBarContainer = event.currentTarget; 
        const rect = progressBarContainer.getBoundingClientRect();
        const clickPositionInPixels = event.clientX - rect.left;
        const barWidthInPixels = progressBarContainer.offsetWidth;
        
        if (barWidthInPixels === 0) return;

        let clickPositionInPercentage = clickPositionInPixels / barWidthInPixels;
        clickPositionInPercentage = Math.max(0, Math.min(1, clickPositionInPercentage));

        this.videoPlayer.currentTime = this.duration * clickPositionInPercentage;
        this.updateProgress(); 
    },
    toggleMute() {
      if (!this.videoPlayer) return;
      this.videoPlayer.muted = !this.videoPlayer.muted;
    },
    handleVolumeChange(event) {
      if (!this.videoPlayer) return;
      const newVolume = parseFloat(event.target.value);
      this.videoPlayer.volume = newVolume;
      this.videoPlayer.muted = newVolume === 0;
    },
    formatTime(timeInSeconds) {
      if (isNaN(timeInSeconds) || timeInSeconds === Infinity || timeInSeconds < 0) {
        return '00:00';
      }
      const minutes = Math.floor(timeInSeconds / 60);
      const seconds = Math.floor(timeInSeconds % 60);
      return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
    },
    toggleFullscreen() {
      if (!this.videoPlayerContainer) return;
      if (!document.fullscreenElement && !document.webkitFullscreenElement && !document.mozFullScreenElement && !document.msFullscreenElement) {
        if (this.videoPlayerContainer.requestFullscreen) {
          this.videoPlayerContainer.requestFullscreen();
        } else if (this.videoPlayerContainer.webkitRequestFullscreen) { 
          this.videoPlayerContainer.webkitRequestFullscreen();
        } else if (this.videoPlayerContainer.mozRequestFullScreen) { 
          this.videoPlayerContainer.mozRequestFullScreen();
        } else if (this.videoPlayerContainer.msRequestFullscreen) { 
          this.videoPlayerContainer.msRequestFullscreen();
        }
      } else {
        if (document.exitFullscreen) {
          document.exitFullscreen();
        } else if (document.webkitExitFullscreen) { 
          document.webkitExitFullscreen();
        } else if (document.mozCancelFullScreen) { 
          document.mozCancelFullScreen();
        } else if (document.msExitFullscreen) { 
          document.msExitFullscreen();
        }
      }
    },
    handleFullscreenChange() {
      this.isFullscreen = !!(document.fullscreenElement || document.webkitFullscreenElement || document.mozFullScreenElement || document.msFullscreenElement);
    },
    
    // Dance Video Player Methods
    handleDanceVideoMetadata() {
      if (!this.danceVideoPlayer) return;
      this.danceDuration = this.danceVideoPlayer.duration;
      this.updateDanceBuffer();
    },
    toggleDancePlay() {
      if (!this.danceVideoPlayer) return;
      if (this.danceVideoPlayer.paused || this.danceVideoPlayer.ended) {
        this.danceVideoPlayer.play().catch(e => console.error("Error playing dance video:", e));
      } else {
        this.danceVideoPlayer.pause();
      }
    },
    updateDanceProgress() {
      if (!this.danceVideoPlayer) return;
      this.danceCurrentTime = this.danceVideoPlayer.currentTime;
      if (this.danceDuration > 0) {
        this.danceProgress = (this.danceVideoPlayer.currentTime / this.danceDuration) * 100;
      } else {
        this.danceProgress = 0;
      }
    },
    updateDanceBuffer() {
      if (!this.danceVideoPlayer || !this.danceVideoPlayer.buffered || this.danceVideoPlayer.buffered.length === 0 || this.danceDuration === 0) {
          this.danceBuffered = 0;
          return;
      }
      let bufferedEnd = 0;
      for (let i = 0; i < this.danceVideoPlayer.buffered.length; i++) {
          if (this.danceVideoPlayer.buffered.start(i) <= this.danceVideoPlayer.currentTime && this.danceVideoPlayer.buffered.end(i) >= this.danceVideoPlayer.currentTime) {
               bufferedEnd = this.danceVideoPlayer.buffered.end(i);
               break;
          }
          if (this.danceVideoPlayer.buffered.length > 0 && (i === this.danceVideoPlayer.buffered.length -1 || bufferedEnd === 0) ) {
              bufferedEnd = this.danceVideoPlayer.buffered.end(this.danceVideoPlayer.buffered.length - 1);
          }
      }
      this.danceBuffered = (bufferedEnd / this.danceDuration) * 100;
    },
    seekDanceVideo(event) {
      if (!this.danceVideoPlayer || this.danceDuration === 0) return;
      const progressBarContainer = event.currentTarget; 
      const rect = progressBarContainer.getBoundingClientRect();
      const clickPositionInPixels = event.clientX - rect.left;
      const barWidthInPixels = progressBarContainer.offsetWidth;
      
      if (barWidthInPixels === 0) return;

      let clickPositionInPercentage = clickPositionInPixels / barWidthInPixels;
      clickPositionInPercentage = Math.max(0, Math.min(1, clickPositionInPercentage));

      this.danceVideoPlayer.currentTime = this.danceDuration * clickPositionInPercentage;
      this.updateDanceProgress(); 
    },
    toggleDanceMute() {
      if (!this.danceVideoPlayer) return;
      this.danceVideoPlayer.muted = !this.danceVideoPlayer.muted;
    },
    toggleDanceFullscreen() {
      if (!this.danceVideoContainer) return;
      if (!document.fullscreenElement && !document.webkitFullscreenElement && !document.mozFullScreenElement && !document.msFullscreenElement) {
        if (this.danceVideoContainer.requestFullscreen) {
          this.danceVideoContainer.requestFullscreen();
        } else if (this.danceVideoContainer.webkitRequestFullscreen) { 
          this.danceVideoContainer.webkitRequestFullscreen();
        } else if (this.danceVideoContainer.mozRequestFullScreen) { 
          this.danceVideoContainer.mozRequestFullScreen();
        } else if (this.danceVideoContainer.msRequestFullscreen) { 
          this.danceVideoContainer.msRequestFullscreen();
        }
      } else {
        if (document.exitFullscreen) {
          document.exitFullscreen();
        } else if (document.webkitExitFullscreen) { 
          document.webkitExitFullscreen();
        } else if (document.mozCancelFullScreen) { 
          document.mozCancelFullScreen();
        } else if (document.msExitFullscreen) { 
          document.msExitFullscreen();
        }
      }
    },
    
    // Keyboard Controls
    handleKeyboardControls(event) {
      const targetTagName = event.target.tagName.toLowerCase();
      if (targetTagName === 'input' || targetTagName === 'textarea' || event.target.isContentEditable) {
          return;
      }

      // Check which video player is active/in viewport
      if (this.videoPlayerContainer && this.isElementInViewport(this.videoPlayerContainer)) {
        const activeElement = document.activeElement;
        const isVinePlayerContext = this.videoPlayerContainer.contains(activeElement) || this.videoPlayer === activeElement || this.isPlaying || (this.videoPlayer && !this.videoPlayer.paused);

        if (isVinePlayerContext) {
          switch (event.key.toLowerCase()) {
            case ' ': 
              event.preventDefault(); 
              this.togglePlay();
              break;
            case 'm': 
              this.toggleMute();
              break;
            case 'f': 
              this.toggleFullscreen();
              break;
          }
        }
      }
      
      if (this.danceVideoContainer && this.isElementInViewport(this.danceVideoContainer)) {
        const activeElement = document.activeElement;
        const isDancePlayerContext = this.danceVideoContainer.contains(activeElement) || this.danceVideoPlayer === activeElement || this.isDancePlaying || (this.danceVideoPlayer && !this.danceVideoPlayer.paused);

        if (isDancePlayerContext) {
          switch (event.key.toLowerCase()) {
            case ' ': 
              event.preventDefault(); 
              this.toggleDancePlay();
              break;
            case 'm': 
              this.toggleDanceMute();
              break;
            case 'f': 
              this.toggleDanceFullscreen();
              break;
          }
        }
      }
    },
    isElementInViewport(el) {
      if (!el) return false;
      const rect = el.getBoundingClientRect();
      const windowHeight = (window.innerHeight || document.documentElement.clientHeight);
      const windowWidth = (window.innerWidth || document.documentElement.clientWidth);

      const vertInView = (rect.top <= windowHeight) && ((rect.top + rect.height) >= 0);
      const horInView = (rect.left <= windowWidth) && ((rect.left + rect.width) >= 0);

      return (vertInView && horInView);
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Inter', sans-serif;
  background-color: #000;
  color: #fff;
  overflow-x: hidden;
}

/* Video Player Wrappers */
.video-player-wrapper {
  position: relative;
}

.video-element {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Big Play Button */
.big-play-button {
  backdrop-filter: blur(8px);
  border: 2px solid rgba(255, 255, 255, 0.3);
  transition: all 0.3s ease;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.big-play-button:hover {
  background-color: rgba(255, 255, 255, 0.3);
  transform: translate(-50%, -50%) scale(1.1);
  border-color: rgba(255, 255, 255, 0.8);
}

.big-play-button i {
  margin-left: 5px; /* Adjusts play icon centering */
}

.controls-bar.always-visible {
  opacity: 1;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}

::-webkit-scrollbar-track {
  background: #0a0a0a;
}

::-webkit-scrollbar-thumb {
  background: #eab308;
  border-radius: 5px;
}

::-webkit-scrollbar-thumb:hover {
  background: #f59e0b;
}

/* Animation classes */
.animate-fadeInUp {
  animation: fadeInUp 0.8s ease-out forwards;
}

.animate-fadeIn {
  animation: fadeIn 1s ease-out forwards;
}

.animate-zoomIn {
  animation: zoomIn 0.6s ease-out forwards;
}

.animate-slideInLeft {
  animation: slideInLeft 0.8s ease-out forwards;
}

.animate-slideInRight {
  animation: slideInRight 0.8s ease-out forwards;
}

.animate-pulse {
  animation: pulse 1.5s infinite ease-in-out;
}

/* Background pattern */
.pattern-bg {
  background-image: radial-gradient(circle, rgba(234, 179, 8, 0.03) 1px, transparent 1px);
  background-size: 20px 20px;
}

/* Aspect ratio utilities */
.aspect-w-16 {
  position: relative;
  padding-bottom: 56.25%;
}

.aspect-w-16 > * {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

/* Blur effects */
.blur-3xl {
  filter: blur(48px);
}

/* Keyframe animations */
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(40px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes zoomIn {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}

@keyframes slideInLeft {
  from { opacity: 0; transform: translateX(-50px); }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes slideInRight {
  from { opacity: 0; transform: translateX(50px); }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}

/* Slow pulse animations for background lights */
@keyframes pulse-slow-1 {
  0%, 100% { opacity: 0.15; transform: scale(1); }
  50% { opacity: 0.3; transform: scale(1.05); }
}
.animate-pulse-slow-1 { animation: pulse-slow-1 8s infinite ease-in-out; }

@keyframes pulse-slow-2 {
  0%, 100% { opacity: 0.1; transform: scale(1); }
  50% { opacity: 0.25; transform: scale(1.03); }
}
.animate-pulse-slow-2 { animation: pulse-slow-2 10s infinite ease-in-out; animation-delay: 1s; }

@keyframes pulse-slow-3 {
  0%, 100% { opacity: 0.08; transform: scale(1); }
  50% { opacity: 0.2; transform: scale(1.06); }
}
.animate-pulse-slow-3 { animation: pulse-slow-3 9s infinite ease-in-out; animation-delay: 0.5s; }

/* Scroll-triggered animations */
.animate-on-scroll {
  opacity: 0;
  transition: opacity 0.3s ease, transform 0.6s ease;
}

.animate-on-scroll.in-view {
  opacity: 1;
}

.animate-on-scroll.in-view.fadeInUp { animation-name: fadeInUp; animation-duration: 0.8s; animation-timing-function: ease-out; animation-fill-mode: forwards; }
.animate-on-scroll.in-view.fadeIn { animation-name: fadeIn; animation-duration: 1s; animation-timing-function: ease-out; animation-fill-mode: forwards; }
.animate-on-scroll.in-view.zoomIn { animation-name: zoomIn; animation-duration: 0.6s; animation-timing-function: ease-out; animation-fill-mode: forwards; }
.animate-on-scroll.in-view.slideInLeft { animation-name: slideInLeft; animation-duration: 0.8s; animation-timing-function: ease-out; animation-fill-mode: forwards; }
.animate-on-scroll.in-view.slideInRight { animation-name: slideInRight; animation-duration: 0.8s; animation-timing-function: ease-out; animation-fill-mode: forwards; }
.animate-on-scroll.in-view.pulse { animation-name: pulse; animation-duration: 1.5s; animation-timing-function: ease-in-out; animation-iteration-count: infinite; }

/* Control buttons */
.control-button {
  transition: all 0.2s ease;
}

.control-button:hover {
  transform: scale(1.1);
  color: #f59e0b;
}

/* Responsive adjustments */
@media (max-width: 640px) {
  #hero h1 {
    font-size: 3.5rem;
    line-height: 1.1;
  }
  
  #hero p {
    font-size: 1rem;
  }
  
  #skills .grid {
    grid-template-columns: 1fr;
  }
  
  /* Adjust video controls for mobile */
  .controls-bar {
    padding: 0.5rem;
  }
  
  .time-display {
    font-size: 0.7rem;
  }
  
  .control-button i {
    font-size: 1rem;
  }
  
  .big-play-button {
    padding: 1.5rem;
  }
  
  .big-play-button i {
    font-size: 2.5rem;
  }
  
  /* Dance video section adjustments */
  #dance-with-me .controls-bar {
    padding: 0.5rem;
  }
  
  #dance-with-me .big-play-button {
    padding: 1.5rem;
  }
  
  #dance-with-me .big-play-button i {
    font-size: 2.5rem;
  }
}

@media (max-width: 768px) {
  #featured-projects .grid {
    grid-template-columns: 1fr;
  }
}
</style>