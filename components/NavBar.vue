<template>
  <nav
    class="
      border-b border-gray-500
      bg-red-50
      p-3
      font-bold
      text-gray-900 text-2xl
      font-mono
      mb-24
      transition transition-color
      hover:text-gray-600
      z-40
      flex
      justify-between
    "
  >
    <div class="z-40 inline-block font-mono uppercase">
      Digital Humanities Catalog<i class="inline-block text-3xl ml-1">+</i>
    </div>
    <a class="text-sm flex pt-2 text-gray-400 hover:text-gray-500">
      <svg
        class="inline-block mr-2 fill-current"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
      >
        <path
          d="M12 2c5.514 0 10 4.486 10 10s-4.486 10-10 10-10-4.486-10-10 4.486-10 10-10zm0-2c-6.627 0-12 5.373-12 12s5.373 12 12 12 12-5.373 12-12-5.373-12-12-12zm1 18h-2v-8h2v8zm-1-12.25c.69 0 1.25.56 1.25 1.25s-.56 1.25-1.25 1.25-1.25-.56-1.25-1.25.56-1.25 1.25-1.25z"
        />
      </svg>
      About
    </a>
  </nav>
</template>

<script>
export default {}
</script>

<style scoped>
@keyframes rotateAnimation {
  0% {
    transform: rotateY(0deg) rotateZ(0deg);
  }
  50% {
    transform: rotateY(180deg) rotateZ(0deg);
  }
  100% {
    transform: rotateY(360deg) rotateZ(0deg);
  }
}
svg {
  animation: rotateAnimation 2s infinite;
}
</style>