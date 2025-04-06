<script>
  import RollingText from "./RollingText.svelte";
  import ProjectGrid from "./ProjectGrid.svelte";
  import { faGithub } from "@fortawesome/free-brands-svg-icons";
  import { FontAwesomeIcon } from "@fortawesome/svelte-fontawesome";
  import { onMount } from "svelte";

  let introContainer;

  onMount(() => {
    if (typeof particlesJS !== "undefined") {
      particlesJS.load("particles-js", "/assets/particles.json", function () {
        console.log("Callback - particles.js config loaded for Intro section");
      });
    }
  });

  const projects = [
    {
      id: 1,
      name: "This page!",
      image: "/images/zima-blue.jpg",
      abstract: "A modern, responsive portfolio website built with SvelteKit",
      description:
        "While it might seem unusual to feature the portfolio itself as a project, it demonstrates my ability to independently design and build a front end from scratch. The site is built with <a class='light-red no-underline dim' href='https://svelte.dev/' target='_blank' rel='noopener noreferrer'>Svelte</a>, styled using <a class='light-red no-underline dim' href='https://tachyons.io/' target='_blank' rel='noopener noreferrer'>Tachyons CSS</a>, and enhanced with a sprinkle of <a class='light-red no-underline dim' href='https://greensock.com/gsap/' target='_blank' rel='noopener noreferrer'>GSAP</a> animations.",
      readMore:
        "If you want to see the code, check out my GitHub profile!<br /> I will try to document my learning process on a blog article <span class=i>(work in progress)</span>.",
      links: ["https://github.com/JBarone90/portfolio"],
    },
    {
      id: 2,
      name: "Dashboard",
      image: "/images/dashboard.png",
      abstract: "This is a brief description of Dashboard.",
      description: "This is a brief description of Dashboard.",
      readMore: "Read more",
      links: ["https://linkto.dashboard.com"],
    },
    // Add more projects here
  ];

  let selectedProject = null;

  // Open the project popover
  function openProject(project) {
    selectedProject = project;
  }

  // Close the project popover
  function closeProject() {
    selectedProject = null;
  }

  function stopPropagation(event) {
    event.stopPropagation();
  }
</script>

<main class="flex flex-column w-100">
  <!-- Intro Section -->
  <section
    id="IntroPage"
    class="bg-black white flex flex-column items-center relative pa2-l pa4-m w-100"
  >
    <div
      id="particles-js"
      class="absolute top-0 left-0 w-100 h-100 z-0 o-90"
    ></div>
    <div
      class="flex flex-column items-center-ns items-start-l pb5-l pb4-ns z-1"
    >
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
    class="RedShadow mv3-l mv3-ns poppins
     br-pill bg-white near-black hover-bg-light-red
     w-20 w-20-ns w-20-m w-20-l mw5 no-underline"
    href="https://www.linkedin.com/in/baronej/"
    target="_blank"
  >
    <h4 class="relative tc f5 f5-ns f5-m f3-l z-1">Get in touch &rarr;</h4>
  </a>
    </div>

    <!-- <div class="flex justify-center justify-end-l justify-end-m w-80-l w-60-m">
      <img
        src="/images/profile_no_background.png"
        alt="Profile"
        class="object-fit-cover"
      />
    </div> -->
  </section>

  <!-- Projects Section -->
  <section
    id="Projects"
    class="flex flex-column mv6-l mv5-ns w-100"
    style="background-color: #F7D488"
  >
    <div class="flex flex-column mv2-ns mv5-l tc pa2-l pa4-m">
      <p class="poppins">
        <span class="f1-l f1-m f3-ns poppins">Portfolio</span>
      </p>
      <!-- Use Grid to render project cards -->
      <div class="flex justify-center">
        <ProjectGrid {projects} {openProject} />
      </div>
    </div>
  </section>

  <!-- Popover Section (Modal) -->
  {#if selectedProject}
    <div
      class="fixed top-0 left-0 w-100 h-100 bg-black-70 flex items-center justify-center z-999"
      onclick={closeProject}
      role="dialog"
      aria-modal="true"
      aria-labelledby="project-title"
      tabindex="-1"
    >
      <div
        class="bg-white pa4 br3 relative mw6 w-90"
        onclick={stopPropagation}
        role="document"
        tabindex="0"
      >
        <button
          class="absolute top-0 right-0 mt2 mr2 pa1 br-pill bw0 bg-transparent pointer grow"
          onclick={closeProject}
          onkeydown={(e) => e.key === "Enter" && closeProject()}
          aria-label="Close project details"
          tabindex="-1"
        >
          ✕
        </button>
        <div class="relative mb3 mr2">
          <img
            src={selectedProject.image}
            alt={selectedProject.name}
            class="w-100 h-100 br3 object-cover"
          />
        </div>
        <h3 id="project-title" class="f3 poppins dark-gray tc mb4">
          {selectedProject.name}
        </h3>
        <h4 class="poppins dark-gray tc mb3">
          {@html selectedProject.abstract}
        </h4>
        <div class="mt5">
          <h5 class="f6 dark-gray mb1">Description</h5>
          <hr class="b--light-gray w-100 mb2" />
          <p class="f6 poppins lh-copy dark-gray mb3">
            {@html selectedProject.description}
          </p>
          <h5 class="f6 dark-gray mt4 mb1">Read More</h5>
          <hr class="b--light-gray w-100 mb2" />
          <p class="f6 poppins lh-copy dark-gray mb3">
            {@html selectedProject.readMore}
          </p>
        </div>

        <!-- Links Section -->
        {#each selectedProject.links as link}
          <a
            href={link}
            target="_blank"
            class="f6 link dim black"
            rel="noopener noreferrer"
          >
            <FontAwesomeIcon icon={faGithub} class="fa-3x" />
          </a>
        {/each}
      </div>
    </div>
  {/if}
</main>
