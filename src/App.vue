<template>
  <div id="bg-dark h-screen">
    <div class="flex" style="height: 88vh;">

    <div class="w-56 bg-black h-full flex-none">
      <div class="p-6">
      <img src="spotifyLogo.png" class="h-10">
      </div>
      <div class="mx-2 mb-5">
        <button v-for="page in pages" v-bind:key="page" @click="setID = page.id" :class="`w-full focus:outline-none text-xs font-semibold rounded px-2 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' : 'text-lightest'}`">
          <i class="material-icons ml-3"> {{page.icon}} </i>
          <p> {{ page.name }} </p>
        </button>
      </div>
    <div class="mx-5">
      <h1 class="mb-3 text-xs text-lightest tracking-widest uppercase">Playlists</h1>
        <button class="flex items-center justify-start opacity-75 hover:opacity-100">
          <img src="add.png" class="h-8 w-8 mr-3 mb-2" style="filter: brightness(0) invert(1);"/>
          <p class="text-sm text-white font-semibold">Create Playlist</p>
        </button>
        <button class="flex items-center justify-start opacity-75 hover:opacity-100">
          <img src="liked.png" class="h-8 w-8 mr-3"/>
          <p class="text-sm text-white font-semibold">Create Playlist</p>
        </button>
        <div class="h-px w-full bg-light my-3"></div>
      </div>
      <div class="mx-5">
        <div class="w-full h-10">
          <p v-for="album in albums" v-bind:key="album" class="text-lightest hover:text-white text-xs py-1"> {{ album.name }} </p>
        </div>
        <button class="flex items-center justify-start text-lightest hover:text-light py-2">
          <img src="download.png" class="mr-3" style="filter: brightness(0) invert(1);"/>
          <p class="text-sm font-semibold">Install App</p>
        </button>
      </div>
      <div class="relative pt-4">
        <div class="w-full h-full flex justify-end items-start opacity-20 hover:opacity-100 absolute">
        <div class="bg-black rounded-full h-5 w-5 mr-2 mt-2">
          <img src="down.png" style="filter: brightness(0) invert(1);">
        </div>
      </div>
      <img src="playing.jpeg"/>
    </div>
  </div>

  <div class="w-full h-full relative bg-black">

    <div class="w-full sticky top-0 py-4 px-6 flex items-center justify-between">
      <div class="flex items-center">
        <button class="rounded-full bg-black w-7 h-7 m-3 text-white">
          <img src="arrowLeft.png" style="filter: brightness(0) invert(1);">
        </button>
        <button class="rounded-full bg-black w-7 h-7 text-white">
          <img src="arrowRight.png" class="ml-1" style="filter: brightness(0) invert(1);">
        </button>
      </div>
      <div class="relative">
        <button class="bg-light rounded-full p-1 flex items-center">
          <img src="avatar.jpg" class="rounded-full h-6 w-6 mr-1">
          <p class="text-white font-semibold text-xs mr-3">Apprehensive Fig</p>
          <img src="arrowDown.png" style="filter: brightness(0) invert(1);"/>
        </button>
        <div class="absolute bg-light w-full rounded mt-1">
          <button class="w-full py-2 text-sm text-lightest hover text-white border-b border-white opacity-75 hover:opacity-100">Account</button>
          <button class="w-full py-2 text-sm text-lightest hover text-white opacity-75 hover:opacity-100">Log Out</button>
        </div>
      </div>
    </div>
  </div>
</div>

  <div class="w-full bg-light" style="height: 12vh;">
  </div>
</div>
</template>

<script>

export default {
  name: 'App',
  data: function() {
    return {
      pages: [
        {id: 'home', name: 'Home', icon: ''},
        {id: 'search', name: 'Search', icon: ''},
        {id: 'library', name: 'Your Library', icon: ''}
      ],
      setID: 'home',
      albums: [
        {name: '80s Hits'}
      ]
    }
  }
}

</script>
<style>

</style>
