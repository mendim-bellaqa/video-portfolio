<template>
  <main class="bg-gray-900 text-gray-100 min-h-screen font-sans">
    <!-- Navigation -->
    <nav class="fixed w-full z-50 bg-gray-900/90 backdrop-blur-md border-b border-gray-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
        <div class="text-xl font-bold">
          <span class="bg-gradient-to-r from-purple-400 to-blue-400 bg-clip-text text-transparent">MENDIM BELLAQA</span>
          <span class="text-gray-300">VIDEO EDITOR</span>
        </div>
        <div class="hidden md:flex space-x-8">
          <a href="#work" class="hover:text-purple-400 transition-colors">Portfolio</a>
          <a href="#skills" class="hover:text-purple-400 transition-colors">Skills</a>
          <a href="#about" class="hover:text-purple-400 transition-colors">About</a>
          <a href="#contact" class="hover:text-purple-400 transition-colors">Contact</a>
        </div>
        <button class="md:hidden text-gray-300">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
          </svg>
        </button>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="pt-32 pb-20 px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto text-center">
        <h1 class="text-4xl sm:text-5xl font-bold mb-6">
          <span class="block mb-4">Professional Video Editor</span>
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-blue-400">Bringing Stories to Life</span>
        </h1>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto mb-8">
          Crafting compelling visual narratives for TV media, social platforms, and digital content
        </p>
        <a href="#work" class="inline-block bg-purple-600 hover:bg-purple-700 text-white px-8 py-3 rounded-lg transition-colors">
          View My Work
        </a>
      </div>
    </section>

    <!-- Featured Work -->
  <section id="work" class="py-16 bg-gray-800/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-bold text-center mb-12">Featured Projects</h2>
      <div class="grid md:grid-cols-3 gap-8">
        <div 
          v-for="(video, index) in videos" 
          :key="index"
          class="relative group overflow-hidden rounded-xl cursor-pointer"
          @click="openModal(video)"
        >
          <div class="relative">
            <video 
              ref="videoPlayer"
              muted 
              loop 
              class="w-full h-64 object-cover transform transition-transform duration-300 group-hover:scale-105"
              @play="updateButton(index)"
              @pause="updateButton(index)"
            >
              <source :src="video.src" type="video/mp4">
            </video>
            <div class="absolute inset-0 flex items-center justify-center">
              <button 
                @click.stop="togglePlay(index)"
                class="p-3 rounded-full bg-gray-900/50 hover:bg-gray-900/80 transition-colors"
              >
                <svg 
                  class="w-8 h-8 text-white"
                  :class="{ 'hidden': video.playing }"
                  fill="none" 
                  stroke="currentColor" 
                  viewBox="0 0 24 24"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"/>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
                </svg>
                <svg 
                  class="w-8 h-8 text-white"
                  :class="{ 'hidden': !video.playing }"
                  fill="none" 
                  stroke="currentColor" 
                  viewBox="0 0 24 24"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 9v6m4-6v6m7-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
                </svg>
              </button>
            </div>
            <div class="absolute inset-0 bg-gradient-to-t from-gray-900/80 via-transparent p-6 flex items-end">
              <div>
                <h3 class="text-white font-bold text-lg">{{ video.title }}</h3>
                <p class="text-purple-400 text-sm">{{ video.category }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
  
  <!-- Video Modal -->
  <div 
    v-if="selectedVideo"
    class="fixed inset-0 z-50 bg-gray-900/90 backdrop-blur-md flex items-center justify-center p-4"
    @click.self="closeModal"
  >
    <div class="relative w-full max-w-4xl">
      <button 
        @click="closeModal"
        class="absolute -top-8 right-0 text-gray-300 hover:text-white transition-colors"
      >
        <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>
      <video 
        ref="modalVideo"
        controls 
        class="w-full rounded-xl shadow-2xl"
        :src="selectedVideo.src"
      ></video>
    </div>
  </div>

    <!-- Skills -->
    <section id="skills" class="py-16">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 class="text-3xl font-bold text-center mb-12">Technical Expertise</h2>
        <div class="grid md:grid-cols-5 gap-6 text-center">
          <div class="p-6 bg-gray-800 rounded-lg">
            <img src="https://img.icons8.com/fluent/512/filmora.png" class="h-12 w-12 mx-auto mb-4" alt="Filmora">
            <p class="font-medium">Wondershare Filmora</p>
          </div>
          <div class="p-6 bg-gray-800 rounded-lg">
            <img src="https://images.dwncdn.net/images/t_app-icon-l/p/53dc8463-7eee-458d-a380-978db5cab90a/856209856/13631_4-77533174-imgingest-2918975849271265413.png" class="h-12 w-12 mx-auto mb-4" alt="After Effects">
            <p class="font-medium">After Effects</p>
          </div>
          <div class="p-6 bg-gray-800 rounded-lg">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRZA7Wuq3CSmhWyJ_uYPsPU3v8lReGBfxJxgQ&s" class="h-12 w-12 mx-auto mb-4" alt="Premiere Pro">
            <p class="font-medium">Premiere Pro</p>
          </div>
          <div class="p-6 bg-gray-800 rounded-lg">
            <img src="https://static.vecteezy.com/system/resources/previews/013/948/546/non_2x/capcut-logo-on-transparent-white-background-free-vector.jpg" class="h-12 w-12 mx-auto mb-4" alt="CapCut">
            <p class="font-medium">CapCut</p>
          </div>
          <div class="p-6 bg-gray-800 rounded-lg">
            <img src="https://icon2.cleanpng.com/20180411/kkq/avu479xq7.webp" class="h-12 w-12 mx-auto mb-4" alt="Cinema 4D">
            <p class="font-medium">Cinema 4D</p>
          </div>
        </div>
      </div>
    </section>

    <!-- About -->
    <section id="about" class="py-16 bg-gray-800/50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div class="relative">
            <img src="https://img.freepik.com/free-photo/3d-renders-computers-living-room_482257-76479.jpg" alt="Editing Studio" class="rounded-xl shadow-2xl">
            <div class="absolute -inset-8 border-2 border-purple-400/30 rounded-xl -z-10"></div>
          </div>
          <div>
            <h2 class="text-3xl font-bold mb-6">About My Work</h2>
            <p class="text-gray-400 mb-6">
              As lead video editor at Arbëria, I've produced over 500+ video pieces including:
            </p>
            <ul class="space-y-3 mb-8">
              <li class="flex items-center">
                <svg class="w-5 h-5 text-purple-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                </svg>
                TV show intros & bumpers
              </li>
              <li class="flex items-center">
                <svg class="w-5 h-5 text-purple-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                </svg>
                Social media shorts (TikTok, Instagram Reels)
              </li>
              <li class="flex items-center">
                <svg class="w-5 h-5 text-purple-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                </svg>
                Documentary storytelling edits
              </li>
              <li class="flex items-center">
                <svg class="w-5 h-5 text-purple-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                </svg>
                Branded content & logo reveals
              </li>
            </ul>
            <a href="#contact" class="inline-block bg-gray-900 hover:bg-gray-800 text-white px-6 py-3 rounded-lg transition-colors">
              Discuss Your Project
            </a>
          </div>
        </div>
      </div>
    </section>


    <!-- Updated About Me Section -->
<section class="py-16 bg-gray-900">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="grid md:grid-cols-2 gap-12 items-center">
      <!-- Profile Image Column -->
      <div class="relative group order-last md:order-first">
        <div class="relative rounded-xl overflow-hidden shadow-2xl">
          <img 
            src="https://media-hosting.imagekit.io/a0abce0a05c0457f/profile.jpg?Expires=1840964711&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=A0VUwC0DO0VZyObJTcPgljddeHA3mVDOPGM6nP8p8d1ODCYIcYLeQ~A-Q~nipVMywwNXIZbpTzA-51pPPtid216FCPgAZGpqXYp6OGSLxgkRf4dvlu7Ak1PWZ0Mu0-K6rEMs9jxr83CMPN3jn6fKivH5AcCk9EkzkbRlMDhy6BBxi52CRs4tJQwGdjKqnY5ZwiiX-NvgFMsG7vaYp-Opo5C01m-h3p0gPqpLSP4m~QpzJS9mTJ4q4dKznqKEM78xWah~ouiWzO94SkuoKPhiGpRjIVX89b1yQO80kGhzbHHUftJVYmpQYAd0DIvMmi1osvVWZHK729ItZtT2JpQyUA__" 
            alt="Mendim Bellaqa" 
            class="w-full h-auto object-cover transform group-hover:scale-105 transition-transform duration-300"
          >
        </div>
        <div class="absolute -inset-8 border-2 border-purple-400/30 rounded-xl -z-10 top-4 left-4"></div>
      </div>

      <!-- Content Column -->
      <div class="space-y-8">
        <h2 class="text-3xl font-bold">Who I Am</h2>
        
        <p class="text-gray-400 text-lg leading-relaxed">
          Hi I'm Mendim Bellaqa, a passionate video editor from Kosovo with over 2 years of professional experience crafting visual stories for television and digital platforms. My journey in video editing began with a fascination for transforming raw footage into emotional narratives.
        </p>

        <!-- Stats Grid -->
        <div class="grid grid-cols-2 gap-4 max-w-sm">
          <div class="p-4 bg-gray-800 rounded-lg text-center">
            <div class="text-purple-400 text-2xl font-bold mb-2">500+</div>
            <div class="text-sm text-gray-300">Projects Completed</div>
          </div>
          <div class="p-4 bg-gray-800 rounded-lg text-center">
            <div class="text-blue-400 text-2xl font-bold mb-2">98%</div>
            <div class="text-sm text-gray-300">Client Satisfaction</div>
          </div>
        </div>

        <!-- Personal Details List -->
        <ul class="space-y-4">
          <li class="flex items-start">
            <svg class="flex-shrink-0 w-5 h-5 text-purple-400 mt-1 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
            </svg>
            <span class="text-gray-400">Based in Prishtina, Kosovo</span>
          </li>
          <li class="flex items-start">
            <svg class="flex-shrink-0 w-5 h-5 text-purple-400 mt-1 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
            </svg>
            <span class="text-gray-400">Fluent in Albanian, English</span>
          </li>
          <li class="flex items-start">
            <svg class="flex-shrink-0 w-5 h-5 text-purple-400 mt-1 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
            </svg>
            <span class="text-gray-400">Film & Photography enthusiast</span>
          </li>
        </ul>
      </div>
    </div>

    <!-- Career Timeline -->
    <div class="mt-16 max-w-3xl mx-auto">
      <h3 class="text-2xl font-bold mb-8 text-center">My Journey</h3>
      <div class="relative pl-8 border-l-2 border-purple-400/20">
        <div class="absolute w-3 h-3 bg-purple-400 rounded-full -left-[7px] top-0"></div>
        <div class="mb-10 pl-6">
          <h4 class="font-semibold text-lg">Lead Video Editor @ Arbëria</h4>
          <p class="text-sm text-gray-400 mt-1">2023 - Present</p>
          <p class="text-gray-400 mt-2 leading-relaxed">
            Creating daily content for prime-time TV shows and managing social media video strategies
          </p>
        </div>
        
        <div class="absolute w-3 h-3 bg-purple-400 rounded-full -left-[7px] top-[160px]"></div>
        <div class="mb-10 pl-6">
          <h4 class="font-semibold text-lg">Personal Video Editings for social media</h4>
          <p class="text-sm text-gray-400 mt-1">2020 - Present</p>
          <p class="text-gray-400 mt-2 leading-relaxed">
            Edited videos for different personal faceless youtube and tiktok accounts.
          </p>
        </div>
      </div>
    </div>
  </div>
</section>

    <!-- Contact -->
    <section id="contact" class="py-16">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="bg-gray-800 rounded-2xl p-8 shadow-xl">
          <h2 class="text-3xl font-bold text-center mb-8">Let's Create Something Amazing</h2>
          <div class="max-w-2xl mx-auto">
            <form class="space-y-6">
              <div>
                <label class="block text-sm font-medium mb-2">Your Name</label>
                <input type="text" class="w-full bg-gray-700 rounded-lg px-4 py-3 focus:ring-2 focus:ring-purple-400">
              </div>
              <div>
                <label class="block text-sm font-medium mb-2">Email Address</label>
                <input type="email" class="w-full bg-gray-700 rounded-lg px-4 py-3 focus:ring-2 focus:ring-purple-400">
              </div>
              <div>
                <label class="block text-sm font-medium mb-2">Project Details</label>
                <textarea rows="4" class="w-full bg-gray-700 rounded-lg px-4 py-3 focus:ring-2 focus:ring-purple-400"></textarea>
              </div>
              <button type="submit" class="w-full bg-purple-600 hover:bg-purple-700 text-white py-3 rounded-lg transition-colors">
                Send Message
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 border-t border-gray-800 py-8">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <div class="flex justify-center space-x-6 mb-4">
          <a href="https://www.linkedin.com/in/mendim-bellaqa/" class="text-gray-400 hover:text-purple-400">
            <span class="sr-only">LinkedIn</span>
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
            </svg>
          </a>
        </div>
        <p class="text-gray-500">&copy; 2025 MENDIM BELLAQA. All rights reserved.</p>
      </div>
    </footer>
  </main>
</template>


<script setup>
import { ref } from 'vue';

const videos = ref([
  {
    src: '/videos/1.mp4',
    title: 'TV Show Intro',
    category: 'MADE WITH FILMORA AND ONLINE FOOTAGES',
    playing: false
  },
  {
    src: '/videos/2-1.mp4',
    title: 'Documentary TV SHOW INTRO',
    category: 'MADE WITH AFTER EFFECT',
    playing: false
  },
  {
    src: '/videos/3.mp4',
    title: 'Music TV SHOW INTRO',
    category: 'MADE WITH AFTER EFFECT',
    playing: false
  }
]);

const selectedVideo = ref(null);
const videoPlayer = ref(null);
const modalVideo = ref(null);

const togglePlay = (index) => {
  const video = videoPlayer.value[index];
  videos.value[index].playing = !videos.value[index].playing;
  video[videos.value[index].playing ? 'play' : 'pause']();
};

const updateButton = (index) => {
  videos.value[index].playing = !videoPlayer.value[index].paused;
};

const openModal = (video) => {
  selectedVideo.value = video;
  nextTick(() => {
    modalVideo.value.play();
  });
};

const closeModal = () => {
  modalVideo.value.pause();
  selectedVideo.value = null;
};
</script>

<style>
/* Add smooth transition for modal */
.video-modal-enter-active,
.video-modal-leave-active {
  transition: opacity 0.3s;
}

.video-modal-enter-from,
.video-modal-leave-to {
  opacity: 0;
}

.video-modal-enter-to,
.video-modal-leave-from {
  opacity: 1;
}
</style>