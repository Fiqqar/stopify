<script>
  export default {
    name: "App",
    data : function () {
      return {
        pages: [
          {id:"home", name:"Home", icon:"home"},
          {id:"search", name:"Search", icon:"search"},
          {id:"library", name:"Library", icon:"bar_chart"},
        ],
        setid: "home",
        albums: [
          {name: "Nonfiksi"},
          {name: "Lagipula Hidup Akan Berakhir"},
          {name: "Me Myself and Dollar Hell"},
          {name: "Skiptracing"},
          {name: "Timeline"},
          {name: "Going Going Gone"},
        ],
        showdropdown: false,
        recents: [
          {src: "/src/assets/image/lampu_kuning.jpeg", title: "Lampu Kuning", artist: "Juicy Luicy"},
          {src: "/src/assets/image/berdansalah.jpeg", title: "Berdansalah, Karir Ini Tak Ada Artinya", artist: "Hindia"},
          {src: "/src/assets/image/botheringyou.jpeg", title: "Am I Bothering You?", artist: "Reality Club"},
          {src: "/src/assets/image/me_myself.jpeg", title: "Me Myself and Dollar Hell", artist: "Mild High Club"},
          {src: "/src/assets/image/no_suprises.jpg", title: "No Suprises", artist: "Radiohead"},
          {src: "/src/assets/image/untitled.jpeg", title: "Untitled", artist: "Rex Orange Country"}
        ]
      }
    }
  }
</script>

<template>
<!-- <span class="material-symbols-outlined">home</span> -->
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" />
  <div class="bg-black" style="height:100vh;">
    <div class="flex" style="height:88vh;">
      <!-- nav -->
      <div class="w-56 bg-black h-full">
        <div class="p-6">
          <img src="./assets/logoname.png" alt="" class="h-20">
        </div>
        <div class="mx-2">
          <button v-for="page in pages" @click="setid=page.id" :class="`text-white w-full rounded px-3 py-2 flex items-center justify-start text-xs font-semibold ${setid===page.id?'bg-gray-600 text-white':'text-lightest'}`">
            <i class="material-symbols-outlined mr-3">
              {{ page.icon }}
            </i>
            <p class="hover:opacity-100 text-sm text-white font-semibold">{{ page.name }}</p>
          </button>
        </div>

        <div class="mx-5">
          <h1 class="mb-3 text-xs text-lightest tracking-widest uppercase">playlist</h1>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100">
            <img src="./assets/image/create.png" alt="" class="h-8 w-8 mr-3">
            <p class="text-sm text-white font-semibold">Create Playlist</p>
          </button>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100">
            <img src="./assets/image/liked.jpg" alt="" class="h-8 w-8 mr-3">
            <p class="text-sm text-white font-semibold">Liked Song</p>
          </button>
          <div class="h-px 2-full bg-white my-3"></div>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100">
            <p class="text-sm text-white font-semibold">Night Music</p>
          </button>
          <div class="h-px w-full bg-light my-3"></div>
        </div>
        <div class="mx-5">
          <div v-for="album in albums" class="w-full h-20 overflow-y-scroll"><p class="hover:text-white text-sm text-white font-semibold py-1">{{ album.name }}</p></div>
        </div>
        <button class="flex items-center justify-start text-gray-300 hover:text-white">
          <i class="material-symbols-outlined mr-3 rounded-full border border-lightest">arrow_downward</i>
          <p class="text-sm font-semibold">Install App</p>
        </button>
      </div>
      <div class="relative">
        <img src="" alt="">
        <div class="w-full h-full flex justify-end items-start bg-yellow-500 absolute">
          <div class="bg-black rounded-full h-8 w-8">
            <i class="material-symbols-outlined text-white">keyboard_arrow_down</i>
          </div>
        </div>
      </div>
      <!-- main content -->
       <div class="w-full h-full relative bg-blue-400">
        <div class="w-full sticky top-0 p-2 flex items-center justify-between">
          <div class="flex items-center">
            <button class="rounded-full bg-black w-8 h-8 text-white">
              <i class="material-symbols-outlined text-xl mr-3">keyboard_arrow_left</i>
            </button>
            <button class="rounded-full bg-black w-8 h-8 text-white">
              <i class="material-symbols-outlined text-xl">keyboard_arrow_right</i>
            </button>
          </div>
          <div class="relative">
              <button class="bg-light rounded-full py-1 px-2 flex items-center" @click="showdropdown = true">
                <img class="rounded-full h-6 w-6" src="" alt="">
                <p class="text-white font-semibold text-xs">fiq</p>
                <i class="material-symbols-outlined text-white">arrow_drop_down</i>
              </button>
              <div class="absolute bg-light w-full rounded mt" v-if="showdropdown === true">
                <button class="w-full text-sm py-2 text-lightest hover text-white border-b border-light" @click="showdropdown = false">Account</button>
                <button class="w-full text-sm py-2 text-lightest hover text-white border-b border-light" @click="showdropdown = false">Log out</button>
              </div>
            </div>
        </div>
        <div class="px-6 py-3 flex items-center container justify-between">
          <h1 class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">Recently Played</h1>
          <h2 class="pr-8 pt-4 text-xs text-lightest uppercase tracking-wider hover:underline">See All</h2>
          <div class="w-full flex-wrap">
            <div v-for="recent in recents" class="p-2 w-48">
              <div class="bg-light w-full h-auto p-5">
                <img :src="`${recent.src}`" alt="" class="h-auto w-full shadow mb-2">
              <h1 class="text-sm font-semibold text-white tracking-wide">{{ recent.title }}</h1>
                <h2 class="text-xs text-lightest tracking-wide">{{ recent.artist }}</h2>
              </div>
            </div>
          </div>
        </div>
       </div>
    </div>
    <!-- play bar -->
     <div class="w-full bg-light">
      
     </div>
  </div>
</template>

<style scoped>

</style>