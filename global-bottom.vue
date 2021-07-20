<template>
  <footer
    v-if="
      $slidev.nav.currentLayout !== 'cover' &&
      $slidev.nav.currentLayout !== 'prisma-title' &&
      $slidev.nav.currentPage !== $slidev.nav.total + 1
    "
    class="absolute bottom-0 left-1 p-2 text-sm w-full"
  >
    <div class="flex">
      <div>
        Cédric Nicoloso&nbsp; | &nbsp;LyonJS chez
        <img
          src="https://georges-public-assets.s3-eu-west-1.amazonaws.com/images/indy/indy-logo.svg"
          height="15"
          class="inline"
          style="height: 16px; margin-bottom: 1px; margin-left: 1px"
        />
        &nbsp;| &nbsp;juillet 2021
      </div>
      <div class="flex-grow">&nbsp;</div>
      <div
        class="mr-1 border rounded-md px-1 text-xs flex items-center"
        style="
          background-color: #e9ecf1;
          border-color: #e9ecf1;
          font-family: 'Roboto Light', sans-serif;
        "
      >
        {{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}
      </div>
    </div>
  </footer>
</template>

<style>
footer {
  font-family: 'Roboto Light', sans-serif;
}
</style>
