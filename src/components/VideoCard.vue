<template>
          <div class="relative group overflow-hidden rounded-xl transition-all duration-500 hover:-translate-y-2" :class="cardClass">
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent z-10 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            
            <video class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-105" loop muted>
              <source :src="src" type="video/mp4" />
              Your browser does not support the video tag.
            </video>
            
            <div class="absolute bottom-0 left-0 right-0 z-20 p-6 transition-all duration-300 transform translate-y-4 group-hover:translate-y-0">
              <span class="inline-block px-3 py-1 text-xs font-semibold bg-purple-500 rounded-full mb-2">
                {{ category }}
              </span>
              <h3 class="text-xl font-semibold">{{ title }}</h3>
            </div>
            
            <div class="absolute inset-0 flex items-center justify-center z-20 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <button class="w-14 h-14 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center hover:bg-white/30 transition">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
              </button>
            </div>
          </div>
        </template>
        
        <script setup>
        defineProps({
          title: String,
          src: String,
          category: {
            type: String,
            default: 'Video'
          },
          cardClass: {
            type: String,
            default: ''
          }
        })
        </script>
        
        <style scoped>
        /* Component-specific styles can go here if needed */
        </style>