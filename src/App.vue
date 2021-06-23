<template>
  <div id="bg-dark h-screen">
    <div class="flex" style="height: 88vh;">

    <div class="w-56 bg-black h-full flex-none">
      <div class="p-6">
      <img src="spotifyLogo.png" class="h-10">
      </div>
      <div class="mx-2">
        <button v-for="page in pages" v-bind:key="page" @click="setID = page.id" :class="`w-full text-xs font-semibold rounded px-2 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' : 'text-lightest'}`">
          <i class="material-icons"> {{page.icon}} </i>
          <p> {{ page.name }} </p>
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
        {id: 'home', name: 'Home', icon: 'home'},
        {id: 'search', name: 'Search', icon: 'search'},
        {id: 'library', name: 'Your Library', icon: 'library'}
      ],
      setID: 'home'
    }
  }
}

</script>
<style>

</style>
