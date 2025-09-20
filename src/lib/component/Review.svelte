<script lang="ts">
  import ReviewStars from "./ReviewStars.svelte";
  export let Stars: number = 0;
  export let Logo: string = "";
</script>

<div class="flex flex-col items-center">
  <div class="w-full flex flex-row gap-4 items-center">
    <img src={Logo} alt="logo" class="h-10 w-10" />
    <slot/>
  </div>
  <ReviewStars stars={Stars} className="mt-8" />
</div>
