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
