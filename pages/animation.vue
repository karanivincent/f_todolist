<template>
  <div class=" w-screen h-screen">
    <div class=" w-1/2 mx-auto">
      <h1 class=" font-semibold text-xl">
        Animation
      </h1>
      <p class="my-2">
        This is a page to try out animation
      </p>
      <button class=" uppercase rounded px-6 py-1" @click="show=!show">
        Click Me
      </button>
      <transition
        enter-active-class="animated bounce"
        leave-active-class="animated rollOut"
      >
        <p v-if="show" class=" font-sans bg-blue-500 rounded inline-block px-6 py-1">
          Tada
        </p>
      </transition>
    </div>
    <div class="mt-12">
      <div class=" ml-64 h-64 w-64 bg-gradient-to-tl from-orange-600   to-pink-700 ">
        Hello
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      show: true
    }
  }

}
</script>

<style>

</style>
