<script>
  import Footer from "../components/Footer.svelte";
  import Header from "../components/Header.svelte";
  import "../app.css";
  let y;
  let innerWidth = 0;
  let innerHeight = 0;

  function goTop() {
    document.body.scrollIntoView();
  }
</script>

<div class="container relative flex flex-column max-w-6xl mx-auto w-100 text-sm sm:text-base min-h-100vh">
  <div class="fixed bottom-0 w-100 duration-200 flex pa3 z-10 {y > 0 ? 'opacity-100 cursor-pointer' : 'opacity-0 pointer-events-none'}">
    <button
      on:click={goTop}
      aria-label="Go to top"
      class="ml-auto br-pill bg-black purple ph3 sm:ph4 hover-bg-dark-gray cursor-pointer aspect-square flex items-center justify-center"
    >
      <i class="fa-solid fa-arrow-up"></i>
    </button>
  </div>
  <Header y={y} {innerHeight} />
  <main class="flex-auto">
    <slot />
  </main>
  <Footer />
</div>
<svelte:window bind:scrollY={y} bind:innerHeight bind:innerWidth />
