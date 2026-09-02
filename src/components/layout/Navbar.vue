<template>
  <div class="Navbar flex justify-between items-center p-3 bg-amber-400 w-full">
    <div>
      <a href="index.html"
        ><img src="./assets/images/logo.png" alt="Logo" class="w-12 h-12 rounded-full"
      /></a>
    </div>

    <div class="navList flex gap-3">
      <div
        class="NavItem items-center justify-center p-2 rounded-3xl text-blue-900 hover:text-white hover:bg-gray-700 cursor-pointer"
      >
        درباره من
      </div>
      <div
        class="NavItem items-center justify-center p-2 rounded-3xl text-blue-900 hover:text-white hover:bg-gray-700 cursor-pointer"
      >
        پروژه ها
      </div>
      <div
        class="NavItem items-center justify-center p-2 rounded-3xl text-blue-900 hover:text-white hover:bg-gray-700 cursor-pointer"
      >
        مهارت ها
      </div>
      <div
        class="NavItem items-center justify-center p-2 rounded-3xl text-blue-900 hover:text-white hover:bg-gray-700 cursor-pointer"
      >
        تماس
      </div>
    </div>

    <div class="Setting">
      <button
        id="SettingBars"
        class="flex items-center justify-center p-2 rounded-md text-gray-700 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
      >
        <font-awesome-icon :icon="['fas', 'bars']" />
      </button>
    </div>
  </div>
</template>

<style></style>

<script></script>
