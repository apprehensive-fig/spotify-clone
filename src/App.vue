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
          <div class="w-full mb-20">
            <p v-for="album in albums" v-bind:key="album" class="text-lightest hover:text-white text-xs py-1"> {{ album.name }} </p>
          </div>
          <button class="flex items-center justify-start text-lightest hover:text-light py-2">
            <img src="download.png" class="mr-1 h-" style="filter: brightness(0) invert(1);"/>
            <p class="text-sm font-semibold">Install App</p>
          </button>
      </div>
    </div>
  <!-- main content -->
  <div class="w-full h-full relative bg-black overflow-y-scroll">
    <!-- header -->
    <div class="w-full sticky top-0 py-4 px-6 flex items-center justify-between bg-dark">
      <div class="flex items-center">
        <button class="rounded-full bg-black w-7 h-7 m-3 text-white">
          <img src="arrowLeft.png" style="filter: brightness(0) invert(1);">
        </button>
        <button class="rounded-full bg-black w-7 h-7 text-white">
          <img src="arrowRight.png" class="ml-1" style="filter: brightness(0) invert(1);">
        </button>
      </div>
      <!-- dropdown -->
      <div class="relative">
        <button class="bg-light rounded-full p-1 flex items-center focus:outline-none">
          <img src="avatar.jpg" class="rounded-full h-6 w-6 mr-1">
          <p class="text-white font-semibold text-xs mr-3">Apprehensive Fig</p>
          <img v-if="showDropdown === false"  @click="showDropdown = true" src="arrowDown.png" style="filter: brightness(0) invert(1);">
          <img v-if="showDropdown === true"  @click="showDropdown = false" src="arrowUp.png" style="filter: brightness(0) invert(1);">
        </button>
        <div v-if="showDropdown === true" class="absolute bg-light w-full rounded mt-1">
          <button @click="showDropdown = false" class="focus:outline-none w-full py-2 text-sm text-lightest hover text-white border-b border-white opacity-75 hover:opacity-100">Account</button>
          <button @click="showDropdown = false" class="focus:outline-none w-full py-2 text-sm text-lightest hover text-white opacity-75 hover:opacity-100">Log Out</button>
        </div>
      </div>
    </div>
    <!-- cards -->
    <div class="px-6 py-3">
      <div class="flex items-center justify-between">
        <h1 class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">Recently played</h1>
        <h2 class="pr-8 pt-4 text-xs text-lightest uppercase tracking-wider hover:underline mb-3">See all</h2>
      </div>
      <div class="w-full flex flex-wrap">
        <div v-for="recent in recents" class="p-2 w-56 relative">
          <div class="absolute w-full h-full flex items-end justify-end p-8">
            <div class="bg-green rounded-full h-10 w-10 flex items-center justify-center opacity-0 hover:opacity-100">
              <img src="play.png" style="filter: brightness(0) invert(1);"/>
            </div>
          </div>
          <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
            <img :src="`${ recent.src }`" class="h-auto w-full shadow mb-2"/>
            <h1 class="text-sm font-semibold text-white tracking wide">{{ recent.title }}</h1>
            <h2 class="text-xs text-lightest tracking-wider pb-5">{{ recent.artist }}</h2>
          </div>
        </div>
      </div>
    </div>
    <div class="px-6 py-3">
      <div class="pl-2">
        <h1 class="text-2xl font-semibold text-white tracking-wider hover:underline">Made for you</h1>
        <h2 class="text-sm text-lightest">Get better recommendations the more you listn</h2>
      </div>
      <div class="w-full flex flex-wrap">
        <div v-for="custom in customs" class="p-2 w-56">
          <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
            <img :src="`${ custom.src }`" class="h-auto w-full shadow mb-2"/>
            <h1 class="text-sm font-semibold text-white tracking wide">{{ custom.title }}</h1>
            <h2 class="text-xs text-lightest tracking-wider pb-5">{{ custom.artist }}</h2>
          </div>
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
        {name: 'All Out 80s'},
        {name: 'This is 90s'},
        {name: 'Starbucks Coffeehouse Pop Radio'},
        {name: 'Backstreet Boys'},
        {name: 'Lofi Fruits Music'}
      ],
      showDropdown: false,
      recents: [
        {src: '', title: 'Dance Pop Hits', artist: 'Spotify'},
        {src: '', title: '2000s Pop', artist: 'Moody Beats Records'},
        {src: '', title: 'All Out 80s', artist: 'Spotify'},
        {src: '', title: 'Liked Songs', artist: 'apprehensive-fig'},
      ],
      customs: [
        {src: '', title: 'Dance Pop Hits', artist: 'Spotify'},
        {src: '', title: '2000s Pop', artist: 'Moody Beats Records'},
        {src: '', title: 'All Out 80s', artist: 'Spotify'},
        {src: '', title: 'Liked Songs', artist: 'apprehensive-fig'},
      ],
    }
  }
}

</script>
<style>

</style>
