<script>
  export let y;

  let tabs = [
    { name: "Projects", link: "#Projects" },
    { name: "About Me", link: "#About Me" },
    { name: "Blog", link: "#Blog" },
  ];
</script>

<header
  class={"sticky z-999 top-0 pl3 pr3 flex items-center justify-between w-100 " +
    (y > 0
      ? "pv2 bg-near-black b--near-black"
      : "pv3 bg-transparent b--transparent")}
>
  <h1 class="fw5">
    <b class="fw7 poppins">Jacopo</b> Barone
  </h1>
  <div class="flex items-center ml2">
    {#each tabs as tab, index}
      <a href={tab.link} class="dim pointer ml2 mr2 transition duration-200 hover-near-purple">
        <p class="white">{tab.name}</p>
      </a>
    {/each}
  </div>
  <a
    href="https://www.linkedin.com/in/jacopobarone/"
    target="_blank"
    class="relative overflow-hidden pa2 br-pill bg-white near-black hover-bg-light-purple"
  >
    <div
      class="absolute top-2 right--100 w-100 h-100 o-20 hover-o-50 z-0"
    ></div>
    <h4 class="relative z-1">Get in touch</h4>
  </a>
</header>
