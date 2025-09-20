<script lang="ts">
  export let stars: number = 0;
  export let className: string = "";
</script>

<div class="{className}">
  <slot/>
  <div class="flex flex-row mt-2 justify-center w-full space-x-2">
    {#each [...Array(5).keys()] as i}
      <img
        src={stars > i ? "./star.svg" : "./empty_star.svg"}
        class="h-6 w-6 select-none"
        draggable="false"
        alt="star"
      />
    {/each}
  </div>
</div>
