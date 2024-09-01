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
        ]
      }
    }
  }
</script>

<template>
  <div class="bg-black" style="height:100vh;">
    <div class="flex" style="height:88vh;">
      <!-- nav -->
      <div class="w-56 bg-black h-full">
        <div class="p-6">
          <img src="./assets/logo.png" alt="" class="h-10">
        </div>
        <div class="mx-2">
          <button v-for="page in pages" @click="setid=page.id" :class="`w-full rounded px-3 py-2 flex items-center justify-start text-xs font-semibold ${setid===page.id?'bg-light text-white':'text-lightest'}`">
            <i class="material-icons mr-">
              {{ page.icon }}
            </i>
            <p>{{ page.name }}</p>
          </button>
        </div>

        <div class="mx-5">
          <h1 class="mb-3 text-xs text-lightest tracking-widest uppercase">playlist</h1>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100">
            <img src="" alt="" class="h-8 w-8 mr-3">
            <p class="text-sm text-white font-semibold">Create Playlist</p>
          </button>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100">
            <img src="" alt="" class="h-8 w-8 mr-3">
            <p class="text-sm text-white font-semibold">Liked Song</p>
          </button>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100">
            <img src="" alt="" class="h-8 w-8 mr-3">
            <p class="text-sm text-white font-semibold">Create Playlist</p>
          </button>
          <div class="h-px w-full bg-light my-3"></div>
        </div>
        <div class="mx-5">
          <div v-for="album in albums" class="w-full h-24 overflow-y-scroll"><p class="text-lightest hover:text-white text-xs py-1">{{ album.name }}</p></div>
        </div>
      </div>
      <!-- main content -->
       <div class="w-full h-full relative bg-blue-400">
        <div class="w-full sticky top-0 p-2"></div>
       </div>
    </div>
    <!-- play bar -->
     <div class="w-full bg-light">
      
     </div>
  </div>
</template>

<style scoped>

</style>
