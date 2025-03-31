<script>
  import { gsap } from "gsap";
  import { onMount } from "svelte";
  import RollingText from "./RollingText.svelte";
</script>

<main class="flex flex-column pa4 mt5">
  <section
    id="IntroPage"
    class="flex flex-column items-center-ns items-start-l mv2-ns mv5-l"
  >
    <div class="flex flex-column items-center-ns items-start-l pb5-l pb4-ns">
      <h2 class="f3 f2-ns f1-l fw6 w-100">
        <span class="poppins light-red">Jacopo</span> Barone
        <br />
        <RollingText stagger={3} class="ph5-ns ph6-l">
          <span class="poppins light-red">Data Scientist</span>
          <span class="poppins light-red">Researcher</span>
        </RollingText>
      </h2>
      <p class="f6 f5-ns f4-m">
        My <span class="light-red"> favorite tech</span> includes JavaScript (NEXT.JS
        or SvelteKit), TailwindCSS, Node.js + Express.js & PostgreSQL or Firebase/Firestore!
      </p>
      <a
        class="RedShadow mv3 mr-auto-l ml0-l f6 f5-ns f4-m poppins
         relative overflow-hidden pa2 ph3 br-pill bg-white near-black hover-bg-washed-yellow
         w-40-ns w-20-l no-underline"
        href="https://www.linkedin.com/in/baronej/"
        target="_blank"
      >
        <h4 class="relative tc z-1">Get in touch &rarr;</h4>
      </a>
    </div>
    <div class="relative ba bw2 flex items-center justify-center">
      <img
        src="/images/profile.jpg"
        alt="Profile"
        class="object-fit-cover z-2 h-70"
      />
    </div>
  </section>
  <section id="Projects" class="flex flex-column mv2-ns mv5-l">
    <div class="flex flex-column mv2-ns mv5-l tc">
      <p class="f6 f4-ns f3-m poppins">
        My <span class="poppins light-red"> Projects</span>
      </p>
    </div>
  </section>
</main>
