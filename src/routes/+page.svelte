<script lang="ts">
  import BorderedButton from "$lib/component/BorderedButton.svelte";
  import Button from "$lib/component/Button.svelte";
  import ReviewStars from "$lib/component/ReviewStars.svelte";
  import Review from "$lib/component/Review.svelte";
  let phone: HTMLDivElement;
  let dropdown: HTMLDivElement;
  let dropdownReviewsContainer: HTMLDivElement;
  let ripple: HTMLDivElement;
  let rippleTrigger: HTMLButtonElement|null = $state(null);
  let secondParagraph: HTMLDivElement;
  let thirdParagraph: HTMLDivElement;
  let searchTriggered = false;

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
    if (searchTriggered) return;
    if (dropdown.className.includes("h-56")) {
      dropdown.className = dropdown.className.replace(/h-56/g, "");
      return (dropdownReviewsContainer.style.opacity = "0%");
    }
    setTimeout(() => {
      dropdownReviewsContainer.style.opacity = "100%";
    }, 100);
    dropdown.className += " h-56";
    searchTriggered = true;
  }

  $effect(() => {
    const PhoneOffset = phone.offsetTop;
    window.addEventListener("scroll", () => sticky(phone, PhoneOffset));
    window.addEventListener("scroll", () => {
      if (window.pageYOffset >= secondParagraph.offsetTop - secondParagraph.offsetHeight) {
        phoneDropdown();
      } else if (searchTriggered) {
        searchTriggered = false;
        phoneDropdown();
      }
    });
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

<Button className="mt-32 mx-auto text-white shadow-2xl" ariaLabel="Get Started" >
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
        <h2 class="font-thin max-w-lg pt-8" bind:this={secondParagraph}>
          search ratings with ez
        </h2>
        <p class="text-black-75 mt-4 max-w-md">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse
          id lectus eu ligula ultrices molestie sit amet ut ex. Fusce id quam
          tristique, malesuada augue a, suscipit libero. Praesent quis venenatis
          leo, quis finibus eros, Sed ut mauris interdum, suscipit orci
          vehicula.
        </p>
      </div>
      <div class="mt-[100%]">
        <h2 class="font-thin max-w-lg" bind:this={thirdParagraph}>found it ! see the rate</h2>
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
              <ReviewStars stars={5} className="mt-8">
                <div class="w-64 h-2 bg-black-50 rounded-full shadow-xl"></div>
                <div
                  class="w-56 h-2 bg-black-50 opacity-50 rounded-full ml-4 shadow-xl mt-1"
                ></div>
              </ReviewStars>
              <ReviewStars stars={4} className="mt-8">
                <div class="w-64 h-2 bg-black-50 rounded-full shadow-xl"></div>
                <div
                  class="w-56 h-2 bg-black-50 opacity-50 rounded-full ml-4 shadow-xl mt-1"
                ></div>
              </ReviewStars>
            </div>
          </div>

          <div class="scale-50 h-0 w-24">
            <Button
              bind:button={rippleTrigger}
              onClick={() => {
                ripple.style.transition = "none";
                ripple.style.transition =
                  "transform 300ms ease, height 300ms ease, width 300ms ease, opacity 300ms ease";
                ripple.style.transform = "scale(1)";
                ripple.style.height = "12rem";
                ripple.style.width = "12rem";
                setTimeout(() => {
                  ripple.style.opacity = "0%";
                }, 300);
                setTimeout(() => {
                  ripple.style.transition = "none";
                  ripple.style.transform = "scale(0)";
                  ripple.style.opacity = "30%";
                  ripple.style.height = "0rem";
                  ripple.style.width = "0rem";
                }, 600);
              }}
            >
              search
              <div
                bind:this={ripple}
                class="bg-white rounded-full absolute transition-[height,width,opacity] duration-300 opacity-30 clip z-0"
                style="height: 0rem; width: 0rem"
              ></div>
            </Button>
          </div>
        </div>

        {#each ["For you:", "Other liker:"] as title}
          <h6 class="mt-8 text-black-75">{title}</h6>
          <hr class="mt-2 text-black-25" />

          <div class="flex flex-col space-y-4">
            {#each [...Array(2).keys()] as i}
              <ReviewStars stars={5 - i} className="mt-8">
                <div class="w-64 h-2 bg-black-25 rounded-full shadow-xl"></div>
                <div
                  class="w-56 h-2 bg-black-10 rounded-full ml-4 shadow-xl mt-1"
                ></div>
              </ReviewStars>
            {/each}
          </div>
        {/each}
      </div>
    </div>
  </div>
</div>
<Review Logo="./apple-logo.svg" Stars={4}>
    <div class="w-64 h-2 bg-black-25 rounded-full shadow-xl"></div>
</Review>
