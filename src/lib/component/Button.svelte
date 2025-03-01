<script lang="ts">
  export let ariaLabel: string = "Button";
  export let className: string = "";
</script>

<button
  class="flex items-center bg-linear-to-r from-primary to-secondary justify-center space-x-2 font-ubuntu text-white text-2xl font-medium px-12 py-6 rounded-full transition-all text-nowrap hover:brightness-105
  hover:scale-95 active:opacity-80 disabled:opacity-50 {className}"
  aria-label={ariaLabel}
>
  <slot />
</button>
