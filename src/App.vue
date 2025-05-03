<template>
  <main class="bg-gray-900 text-white min-h-screen font-sans overflow-x-hidden">
    <!-- Navigation -->
    <nav class="fixed w-full z-50 bg-gray-900/80 backdrop-blur-md border-b border-gray-800">
      <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
        <div class="text-2xl font-bold bg-gradient-to-r from-purple-500 to-blue-400 bg-clip-text text-transparent">
          CINEMATIC<span class="text-white">STUDIO</span>
        </div>
        <div class="hidden md:flex space-x-8">
          <a href="#home" class="hover:text-purple-400 transition-all duration-300">Home</a>
          <a href="#about" class="hover:text-purple-400 transition-all duration-300">About</a>
          <a href="#work" class="hover:text-purple-400 transition-all duration-300">Portfolio</a>
          <a href="#contact" class="hover:text-purple-400 transition-all duration-300">Contact</a>
        </div>
        <button class="md:hidden">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
        </button>
      </div>
    </nav>

    <!-- Hero -->
    <section id="home" class="relative h-screen flex items-center justify-center text-center overflow-hidden">
      <div class="absolute inset-0 bg-black/50 z-10"></div>
      <video autoplay muted loop class="absolute inset-0 w-full h-full object-cover">
        <source src="https://assets.mixkit.co/videos/preview/mixkit-waves-in-the-water-1164-large.mp4" type="video/mp4">
      </video>
      
      <div class="relative z-20 px-6 max-w-4xl mx-auto">
        <h1 class="text-5xl md:text-7xl font-bold mb-6 animate-fade-in">
          <span class="bg-gradient-to-r from-purple-400 to-blue-400 bg-clip-text text-transparent">Mendim</span> 
          <span class="text-white">Bellaqa</span>
        </h1>
        <p class="text-xl md:text-2xl mb-8 text-gray-300 animate-fade-in-up delay-100">
          Crafting visual stories that captivate and inspire
        </p>
        <div class="animate-fade-in-up delay-200">
          <a href="#work" class="inline-block bg-gradient-to-r from-purple-600 to-blue-500 text-white px-8 py-3 rounded-full font-semibold hover:shadow-lg hover:shadow-purple-500/30 transition-all duration-300 transform hover:-translate-y-1">
            View My Work
          </a>
        </div>
      </div>
      
      <div class="absolute bottom-10 left-0 right-0 z-20 animate-bounce">
        <a href="#about" class="block w-10 h-10 mx-auto border-2 border-white rounded-full flex items-center justify-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </a>
      </div>
    </section>

    <!-- About -->
    <section id="about" class="relative px-6 py-20 max-w-6xl mx-auto">
      <div class="absolute -left-20 -top-20 w-64 h-64 bg-purple-600 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-blob"></div>
      <div class="absolute -right-20 -bottom-20 w-64 h-64 bg-blue-600 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-blob animation-delay-2000"></div>
      
      <div class="relative z-10">
        <h2 class="text-3xl md:text-4xl font-bold mb-12 text-center">
          <span class="relative inline-block">
            <span class="relative z-10">About Me</span>
            <span class="absolute bottom-0 left-0 w-full h-2 bg-purple-500/30 -rotate-1 z-0"></span>
          </span>
        </h2>
        
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div class="space-y-6">
            <p class="text-lg text-gray-300 leading-relaxed">
              I'm a passionate video editor and cinematographer with over 2 years of experience creating compelling visual narratives. Specializing in cinematic storytelling, corporate videos, and social media content, I bring ideas to life through the art of motion pictures.
            </p>
            <p class="text-lg text-gray-300 leading-relaxed">
              My approach combines technical expertise with creative vision to deliver content that resonates with audiences and achieves business objectives.
            </p>
            
            <div class="pt-6">
              <h3 class="text-xl font-semibold mb-4">My Skills</h3>
              <div class="grid grid-cols-2 gap-4">
                <div class="flex items-center">
                  <div class="w-2 h-2 bg-purple-500 rounded-full mr-2"></div>
                  <span>Wondershare Filmora</span>
                </div>
                <div class="flex items-center">
                  <div class="w-2 h-2 bg-purple-500 rounded-full mr-2"></div>
                  <span>After Effects</span>
                </div>
                <div class="flex items-center">
                  <div class="w-2 h-2 bg-purple-500 rounded-full mr-2"></div>
                  <span>Premiere Pro</span>
                </div>
                <div class="flex items-center">
                  <div class="w-2 h-2 bg-purple-500 rounded-full mr-2"></div>
                  <span>Cinema 4D</span>
                </div>
                <div class="flex items-center">
                  <div class="w-2 h-2 bg-purple-500 rounded-full mr-2"></div>
                  <span>Color Grading</span>
                </div>
                <div class="flex items-center">
                  <div class="w-2 h-2 bg-purple-500 rounded-full mr-2"></div>
                  <span>Motion Graphics</span>
                </div>
              </div>
            </div>
          </div>
          
          <div class="relative group">
            <div class="absolute -inset-2 bg-gradient-to-r from-purple-600 to-blue-500 rounded-lg blur opacity-75 group-hover:opacity-100 transition duration-200 animate-tilt"></div>
            <div class="relative bg-gray-800 rounded-lg overflow-hidden h-96">
              <img src="https://images.unsplash.com/photo-1551269901-5c5e14c25df7?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" alt="Alex working" class="w-full h-full object-cover transform group-hover:scale-105 transition duration-500">
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Portfolio -->
    <section id="work" class="px-6 py-20 bg-gray-800/50">
      <div class="max-w-6xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-4 text-center">
          <span class="relative inline-block">
            <span class="relative z-10">My Portfolio</span>
            <span class="absolute bottom-0 left-0 w-full h-2 bg-blue-500/30 -rotate-1 z-0"></span>
          </span>
        </h2>
        <p class="text-lg text-gray-400 text-center mb-12 max-w-2xl mx-auto">
          A selection of my recent work across different genres and styles
        </p>
        
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <VideoCard 
            title="Cinematic Short Film" 
            src="https://assets.mixkit.co/videos/preview/mixkit-tree-with-yellow-flowers-1173-large.mp4"
            category="Narrative"
            class="hover:shadow-purple-500/20"
          />
          <VideoCard 
            title="Corporate Branding" 
            src="https://assets.mixkit.co/videos/preview/mixkit-man-under-multicolored-lights-1237-large.mp4"
            category="Commercial"
            class="hover:shadow-blue-500/20"
          />
          <VideoCard 
            title="Music Video" 
            src="https://assets.mixkit.co/videos/preview/mixkit-woman-dancing-under-neon-lights-1230-large.mp4"
            category="Entertainment"
            class="hover:shadow-pink-500/20"
          />
        </div>
        
        <div class="text-center mt-16">
          <button class="border-2 border-purple-500 text-purple-500 px-8 py-3 rounded-full font-semibold hover:bg-purple-500 hover:text-white transition-all duration-300">
            View Full Portfolio
          </button>
        </div>
      </div>
    </section>

    <!-- Testimonials -->
    <section class="py-20 bg-gray-900">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-3xl md:text-4xl font-bold mb-12 text-center">
          <span class="relative inline-block">
            <span class="relative z-10">Client Testimonials</span>
            <span class="absolute bottom-0 left-0 w-full h-2 bg-purple-500/30 -rotate-1 z-0"></span>
          </span>
        </h2>
        
        <div class="grid md:grid-cols-2 gap-8">
          <div class="bg-gray-800/50 p-8 rounded-xl border border-gray-700 hover:border-purple-500 transition-all duration-300">
            <div class="flex items-center mb-4">
              <div class="w-12 h-12 rounded-full overflow-hidden mr-4">
                <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Sarah Johnson" class="w-full h-full object-cover">
              </div>
              <div>
                <h4 class="font-bold">Sarah Johnson</h4>
                <p class="text-sm text-gray-400">Marketing Director, TechCorp</p>
              </div>
            </div>
            <p class="text-gray-300 italic">
              "Alex transformed our corporate video into a cinematic masterpiece. His attention to detail and creative vision exceeded all our expectations."
            </p>
            <div class="flex mt-4">
              <svg v-for="star in 5" :key="star" xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
            </div>
          </div>
          
          <div class="bg-gray-800/50 p-8 rounded-xl border border-gray-700 hover:border-blue-500 transition-all duration-300">
            <div class="flex items-center mb-4">
              <div class="w-12 h-12 rounded-full overflow-hidden mr-4">
                <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="Michael Chen" class="w-full h-full object-cover">
              </div>
              <div>
                <h4 class="font-bold">Michael Chen</h4>
                <p class="text-sm text-gray-400">CEO, Creative Agency</p>
              </div>
            </div>
            <p class="text-gray-300 italic">
              "Working with Alex was a game-changer for our agency. His ability to understand brand identity and translate it into compelling video content is unmatched."
            </p>
            <div class="flex mt-4">
              <svg v-for="star in 5" :key="star" xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section id="contact" class="px-6 py-20 max-w-4xl mx-auto">
      <h2 class="text-3xl md:text-4xl font-bold mb-12 text-center">
        <span class="relative inline-block">
          <span class="relative z-10">Get In Touch</span>
          <span class="absolute bottom-0 left-0 w-full h-2 bg-blue-500/30 -rotate-1 z-0"></span>
        </span>
      </h2>
      
      <div class="grid md:grid-cols-2 gap-12">
        <div>
          <h3 class="text-xl font-semibold mb-4">Contact Information</h3>
          <p class="text-gray-300 mb-6">
            Have a project in mind or want to discuss potential collaboration? Feel free to reach out!
          </p>
          
          <div class="space-y-4">
            <div class="flex items-start">
              <div class="bg-purple-500/10 p-2 rounded-lg mr-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
              </div>
              <div>
                <h4 class="font-medium">Email</h4>
                <a href="mailto:alex@cinematicstudio.com" class="text-gray-400 hover:text-purple-400 transition">alex@cinematicstudio.com</a>
              </div>
            </div>
            
            <div class="flex items-start">
              <div class="bg-blue-500/10 p-2 rounded-lg mr-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                </svg>
              </div>
              <div>
                <h4 class="font-medium">Phone</h4>
                <a href="tel:+1234567890" class="text-gray-400 hover:text-blue-400 transition">+1 (234) 567-890</a>
              </div>
            </div>
          </div>
        </div>
        
        <div class="bg-gray-800/50 p-8 rounded-xl border border-gray-700">
          <h3 class="text-xl font-semibold mb-6">Send Me a Message</h3>
          <form class="space-y-4">
            <div>
              <label for="name" class="block text-sm font-medium text-gray-300 mb-1">Name</label>
              <input type="text" id="name" class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent">
            </div>
            <div>
              <label for="email" class="block text-sm font-medium text-gray-300 mb-1">Email</label>
              <input type="email" id="email" class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent">
            </div>
            <div>
              <label for="message" class="block text-sm font-medium text-gray-300 mb-1">Message</label>
              <textarea id="message" rows="4" class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent"></textarea>
            </div>
            <button type="submit" class="w-full bg-gradient-to-r from-purple-600 to-blue-500 text-white px-6 py-3 rounded-lg font-semibold hover:shadow-lg hover:shadow-purple-500/30 transition-all duration-300">
              Send Message
            </button>
          </form>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 border-t border-gray-800 py-8">
      <div class="max-w-6xl mx-auto px-6 text-center">
        <div class="flex justify-center mb-6">
          <div class="text-2xl font-bold bg-gradient-to-r from-purple-500 to-blue-400 bg-clip-text text-transparent">
            CINEMATIC<span class="text-white">STUDIO</span>
          </div>
        </div>
        <p class="text-gray-400 mb-6">
          Crafting visual stories that captivate and inspire audiences worldwide.
        </p>
        <p class="text-gray-500 text-sm">
          © 2023 Cinematic Studio. All rights reserved.
        </p>
      </div>
    </footer>
  </main>
</template>

<script setup>
import VideoCard from './components/VideoCard.vue'
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

@keyframes fade-in {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes fade-in-up {
  from { 
    opacity: 0;
    transform: translateY(20px);
  }
  to { 
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes blob {
  0% { transform: translate(0px, 0px) scale(1); }
  33% { transform: translate(30px, -50px) scale(1.1); }
  66% { transform: translate(-20px, 20px) scale(0.9); }
  100% { transform: translate(0px, 0px) scale(1); }
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

@keyframes tilt {
  0% { transform: rotate(0deg); }
  25% { transform: rotate(1deg); }
  75% { transform: rotate(-1deg); }
  100% { transform: rotate(0deg); }
}

.animate-fade-in {
  animation: fade-in 1s ease-out forwards;
}

.animate-fade-in-up {
  animation: fade-in-up 0.8s ease-out forwards;
}

.delay-100 {
  animation-delay: 100ms;
}

.delay-200 {
  animation-delay: 200ms;
}

.animate-blob {
  animation: blob 7s infinite;
}

.animation-delay-2000 {
  animation-delay: 2s;
}

.animate-bounce {
  animation: bounce 2s infinite;
}

.animate-tilt {
  animation: tilt 6s ease-in-out infinite;
}

::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #1a1a1a;
}

::-webkit-scrollbar-thumb {
  background: #4f46e5;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #6366f1;
}

body {
  font-family: 'Poppins', sans-serif;
  scroll-behavior: smooth;
}
</style>