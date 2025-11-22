<script lang="ts">
  export let question: string = "";
  let isAnswerVisible: boolean = false;
</script>

<div class="flex space-x-4 flex-col">
  <div class="flex space-x-2">
    <h6 class="text-primary">{isAnswerVisible ? "-" : "+"}</h6>
    <button
      class="{isAnswerVisible ? 'text-black-75' : 'text-black-50'} font-bold font-ubuntu text-xl w-full text-start"
      on:click={() => {
        isAnswerVisible = !isAnswerVisible;
      }}
      aria-label="show answer"
    >
      {question}
    </button>
  </div>

  <p
    class="{isAnswerVisible
      ? ''
      : 'hidden'} text-black-75 ml-8 font-ubuntu text-xl font-medium mt-2"
  >
    <slot />
  </p>

  <hr class="mt-4 text-black-25 w-full" />
</div>
