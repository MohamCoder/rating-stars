<script>
  import BorderedButton from "$lib/component/BorderedButton.svelte";
  import Button from "$lib/component/Button.svelte";
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

<div class="mt-32 flex items-center justify-between mx-64">
  <span>
    <h1>find ratings <br /> & upload <br /> yours</h1>
    <p class="text-black-75 max-w-md">
      Enim eligendi culpa iusto consequuntur distinctio impedit ipsa quas eos
      ipsam ipsum numquam maiores repellendus pariatur dicta aperiam, eaque
      neque eius exercitationem?
    </p>
  </span>
  <img
    src="/undraw_reviews_ukai.svg"
    class="h-[352px] mt-16 select-none"
    alt="ratings"
  />
</div>

<Button className ="mt-32 mx-auto text-white" ariaLabel="Get Started">
  <p>Get Started</p>
  <img src="/arrow_down.svg" height="24px" width="24x" class="" alt="scroll down" />
</Button>
