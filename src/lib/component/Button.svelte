<script lang="ts">
  export let ariaLabel: string = "Button";
  export let className: string = "";
  export let onClick = () => {};
  let button: HTMLButtonElement|null=null;
  export { button };
</script>

<button
  class="relative flex items-center bg-linear-to-r from-primary to-secondary justify-center space-x-2 font-ubuntu text-white text-2xl font-medium px-12 py-6 rounded-full transition-all text-nowrap hover:brightness-105
  hover:scale-95 active:opacity-80 disabled:opacity-50 overflow-hidden {className}"
  bind:this={button}
  aria-label={ariaLabel}
  on:click={() => {
    onClick();
  }}
>
  <slot />
</button>
