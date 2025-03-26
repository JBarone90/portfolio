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

<div
  class="relative flex flex-column mw6 mw8-ns center
 w-100 w-100-l f6-ns f5-l min-vh-100 ph2-ns ph4-l "
>
  <div
    class={"grow dib fixed bottom-0 w-auto flex pa3 z-999 " +
      (y > 0 ? "o-100 pe-auto" : "o-0 pe-none")}
  >
    <button
      on:click={goTop}
      aria-label="Go to top"
      class="br-pill bg-white near-black ph4 pv2 flex items-center justify-center "
    >
      <i class="fa-solid fa-arrow-up"></i>
    </button>
  </div>
  <Header {y} {innerHeight} />
  <main class="flex-auto w-100">
    <slot />
  </main>
  <Footer />
  <div class="h3 h4-l"></div>
</div>
<svelte:window bind:scrollY={y} bind:innerHeight bind:innerWidth />
