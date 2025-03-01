<script lang="ts">
  export let ariaLabel: string = "Button";
  export let className: string = "";
</script>

<button
  aria-label={ariaLabel}
  class="flex items-center justify-center space-x-2 bg-white font-ubuntu text-black text-2xl font-medium px-12 py-6 border-black border-4 rounded-full transition-all text-nowrap hover:bg-black hover:text-white
  hover:scale-95 active:bg-black-75 disabled:text-black-50 {className}"
>
  <slot />
</button>
