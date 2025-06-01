<template>
  <div v-if="showPromo" id="promo"
    class="flex items-center justify-between border-b border-indigo-600 bg-indigo-500 px-4 py-2 text-gray-900"
  >
    <span> </span>
  
    <p class="text-center font-medium">
      Order Website Termurah di
      <a href="#" class="inline-block underline"> Safcil Dev </a>
    </p>
  
    <button
      type="button"
      aria-label="Dismiss"
      @click="hidePromo"
      class="rounded border border-indigo-600 bg-blue p-1.5 shadow-sm transition-colors hover:bg-gray-600"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="size-5"
      >
        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
      </svg>
    </button>
  </div>
</template>

<script>
export default {
    data() {
      return {
        showPromo: true
      };
    },
    methods: {
        hidePromo() {
            this.showPromo = false;
        }
    },
}
</script>