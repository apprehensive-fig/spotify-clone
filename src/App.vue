<template>
  <div id="bg-dark h-screen">
    <div class="flex" style="height: 88vh;">

    <div class="w-56 bg-black h-full flex-none">
      <div class="p-6">
      <img src="spotifyLogo.png" class="h-10">
      </div>
      <div class="mx-2 mb-5">
        <button v-for="page in pages" v-bind:key="page" @click="setID = page.id" :class="`w-full text-xs font-semibold rounded px-2 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' : 'text-lightest'}`">
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
      </div>
    </div>
    <div class="w-full h-full relative">

      <div class="w-full sticky top-0 p-2">
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
      setID: 'home'
    }
  }
}

</script>
<style>

</style>
