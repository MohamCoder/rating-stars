<script lang="ts">
  import ReviewStars from "./ReviewStars.svelte";
  export let stars: number = 0;
  export let logo: string = "";
  export let className: string = "";
</script>

<div class="flex flex-col items-center {className}">
  <div class="w-full flex flex-row gap-4 items-center">
    <img src={logo} alt="logo" class="h-7 w-7" />
    <slot/>
  </div>
  <ReviewStars stars={stars} className="mt-2" />
</div>
