<template>
  <footer v-if="$slidev.nav.currentLayout !== 'cover'" class="absolute bottom-0 left-1 p-2">
    Cedric Nicoloso - LyonJS #68
    {{$slidev.nav.currentLayout}}
  </footer>
</template>
