<script lang="ts">
  import BorderedButton from "$lib/component/BorderedButton.svelte";
  import Button from "$lib/component/Button.svelte";
  import Review from "$lib/component/Review.svelte";
  let phone: HTMLDivElement;
  let dropdown: HTMLDivElement;
  let dropdownReviewsContainer: HTMLDivElement;

  function sticky(container: HTMLDivElement, offset: number) {
    if (window.pageYOffset >= offset) {
      container.style.position = "fixed";
      container.style.translate = "-100% 0rem";
    } else {
      container.style.position = "relative";
      container.style.translate = "0 0";
    }
  }

  function phoneDropdown() {
    if (dropdown.className.includes("h-56")) {
      dropdown.className = dropdown.className.replace(/h-56/g, "");
      return (dropdownReviewsContainer.style.opacity = "0%");
    }
    setTimeout(() => {
      dropdownReviewsContainer.style.opacity = "100%";
    }, 100);
    dropdown.className += " h-56";
  }

  $effect(() => {
    const phoneOffset = phone.offsetTop;
    window.addEventListener("scroll", () => sticky(phone, phoneOffset));
  });
</script>

<div class="main-star"></div>

<navbar class="flex items-center justify-between mx-64 mt-8 h-10">
  <div class="flex items-center space-x-16 select-none">
    <p class="cursor-pointer">STAR</p>
    <p class="text-black-75 cursor-pointer">home</p>
    <p class="text-black-75 cursor-pointer">upload</p>
    <p class="text-black-75 cursor-pointer">pricing</p>
  </div>
  <div class="flex items-center space-x-8 scale-[.6]">
    <BorderedButton ariaLabel="Login">
      <p>Login</p>
    </BorderedButton>
    <Button ariaLabel="Sign Up">
      <p>Sign Up</p>
    </Button>
  </div>
</navbar>

<hero class="mt-32 flex items-center justify-between mx-64">
  <span>
    <h1>find ratings <br /> & upload <br /> yours</h1>
    <p class="text-black-75 max-w-md">
      Enim eligendi culpa iusto consequuntur distinctio impedit ipsa quas eos
      ipsam ipsum numquam maiores repellendus pariatur dicta aperiam, Eaque
      neque eius exercitationem?
    </p>
  </span>
  <img
    draggable="false"
    src="./undraw_reviews_ukai.svg"
    class="h-[22rem] mt-16 select-none"
    alt="ratings"
  />
</hero>

<Button className="mt-32 mx-auto text-white shadow-2xl" ariaLabel="Get Started">
  <p>Get Started</p>
  <img
    src="/arrow_down.svg"
    class="h-6 w-6 select-none"
    draggable="false"
    alt="scroll down"
  />
</Button>

<div class=" mt-32 mx-64 mb-4 flex flex-col items-center">
  <p class="mb-4 text-black-75">we do</p>
  <div class="flex items-center justify-between w-full">
    {#each ["music", "art", "shopping", "movies", "upload"] as star}
      <div>
        <div class="star">
          <img
            class="select-none h-8 w-8 translate-10"
            src={`./${star}.svg`}
            draggable="false"
            alt={star}
          />
        </div>
        <p class="text-black-50 text-center">{star}</p>
      </div>
    {/each}
  </div>
</div>

<div class="h-[300rem] w-full bg-black-5 mt-16 py-8">
  <div class="flex justify-between mx-64">
    <div class="mt-16">
      <h2 class="font-thin max-w-lg">find ratings with a click of a button</h2>
      <p class="text-black-75 mt-4 max-w-md">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse id
        lectus eu ligula ultrices molestie sit amet ut ex. Fusce id quam
        tristique, malesuada augue a, suscipit libero. Praesent quis venenatis
        leo, quis finibus eros, Sed ut mauris interdum, suscipit orci vehicula.
      </p>
      <div class="mt-[100%] py-24">
        <h2 class="font-thin max-w-lg">search ratings with ez</h2>
        <p class="text-black-75 mt-4 max-w-md">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse
          id lectus eu ligula ultrices molestie sit amet ut ex. Fusce id quam
          tristique, malesuada augue a, suscipit libero. Praesent quis venenatis
          leo, quis finibus eros, Sed ut mauris interdum, suscipit orci
          vehicula.
        </p>
      </div>
      <div class="mt-[100%]">
        <h2 class="font-thin max-w-lg">found it ! see the rate</h2>
        <p class="text-black-75 mt-4 max-w-md">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse
          id lectus eu ligula ultrices molestie sit amet ut ex. Fusce id quam
          tristique, malesuada augue a, suscipit libero. Praesent quis venenatis
          leo, quis finibus eros, Sed ut mauris interdum, suscipit orci
          vehicula.
        </p>
      </div>
    </div>

    <div>
      <div
        class="h-[52rem] top-8 w-[26.75rem] px-8 border border-black rounded-[48px]"
        bind:this={phone}
      >
        <div class="flex w-full mr-1 mt-8">
          <div
            class="w-64 h-10 border rounded-full border-black-25 flex items-center"
          >
            <div
              class="ml-2 mr-16 w-full h-3 bg-black-10 rounded-full shadow-xl"
            ></div>
          </div>
          <div
            class="w-[22.75rem] h-0 bg-black-25 shadow-2xl rounded-[24px] absolute mt-12 transition-all"
            bind:this={dropdown}
          >
            <div
              class="flex flex-col space-y-4 px-8 opacity-0 transition-all"
              bind:this={dropdownReviewsContainer}
            >
              <Review stars={5} className="mt-8">
                <div class="w-64 h-2 bg-black-50 rounded-full shadow-xl"></div>
                <div
                  class="w-56 h-2 bg-black-50 opacity-50 rounded-full ml-4 shadow-xl mt-1"
                ></div>
              </Review>
              <Review stars={4} className="mt-8">
                <div class="w-64 h-2 bg-black-50 rounded-full shadow-xl"></div>
                <div
                  class="w-56 h-2 bg-black-50 opacity-50 rounded-full ml-4 shadow-xl mt-1"
                ></div>
              </Review>
            </div>
          </div>

          <div class="scale-50 h-0 w-24">
            <Button onClick={() => phoneDropdown()}>search</Button>
          </div>
        </div>

        {#each ["For you:", "Other liker:"] as title}
          <h6 class="mt-8 text-black-75">{title}</h6>
          <hr class="mt-2 text-black-25" />

          <div class="flex flex-col space-y-4">
            {#each [...Array(2).keys()] as i}
              <Review stars={5 - i} className="mt-8">
                <div class="w-64 h-2 bg-black-25 rounded-full shadow-xl"></div>
                <div
                  class="w-56 h-2 bg-black-10 rounded-full ml-4 shadow-xl mt-1"
                ></div>
              </Review>
            {/each}
          </div>
        {/each}
      </div>
    </div>
  </div>
</div>
