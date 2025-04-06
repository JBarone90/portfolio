<script>
  export let y;

  let tabs = [
    { name: "Projects", link: "#Projects" },
    { name: "About Me", link: "#About Me" },
    { name: "Blog", link: "#Blog" },
  ];
</script>

<header
  class={"sticky z-999 pl3 pr3 flex items-center justify-between w-100 " +
    (y > 0
      ? "bg-lightest-blue b--lightest-blue"
      : "bg-transparent b--transparent")}
>
  <h1 class="fw5 f2-l f3-m f4-ns f5">
    <b class="fw7 poppins">Jacopo</b> Barone
  </h1>
  <div class="flex items-center f4-l f5-m f6-ns f7">
    {#each tabs as tab, index}
      <a
        href={tab.link}
        class="dim ml2 mr2 transition duration-200 no-underline"
      >
        <p class="black b">{tab.name}</p>
      </a>
    {/each}
  </div>
</header>
