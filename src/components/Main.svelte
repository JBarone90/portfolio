<script>
  import RollingText from "./RollingText.svelte";
  import ProjectGrid from "./ProjectGrid.svelte";

  const projects = [
    {
      id: 1,
      name: "Project 1",
      image: "/images/zima-blue.jpg",
      description: "This is a brief description of Project 1.",
      links: ["https://linkto.project1.com", "https://github.com/project1"],
    },
    {
      id: 2,
      name: "Project 2",
      image: "/images/zima-blue.jpg",
      description: "This is a brief description of Project 2.",
      links: ["https://linkto.project2.com", "https://github.com/project2"],
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

<main class="flex flex-column pa2-l pa4-m mt2-l mt4-m">
  <!-- Intro Section -->
  <section
    id="IntroPage"
    class="bg-white-20 flex flex-column items-center mv6-l mv5-ns"
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
        class="RedShadow mv3-l mv3-ns f5-ns f4-m poppins
        overflow-hidden pa2 ph3 br-pill bg-white near-black hover-bg-washed-yellow
         w-40-ns w-20-l no-underline"
        href="https://www.linkedin.com/in/baronej/"
        target="_blank"
      >
        <h4 class="relative tc z-1">Get in touch &rarr;</h4>
      </a>
    </div>

    <div class="flex justify-center justify-end-l w-100">
      <img
        src="/images/profile.jpg"
        alt="Profile"
        class="object-fit-cover z-2 h-70"
      />
    </div>
  </section>

  <!-- Projects Section -->
  <section id="Projects" class="bg-white-60 flex flex-column mv6-l mv5-ns">
    <div class="flex flex-column mv2-ns mv5-l tc">
      <p class="poppins">
        <span class="f1-l f1-m f3-ns poppins light-red">Portfolio</span>
      </p>
      <!-- Use Grid to render project cards -->
      <ProjectGrid {projects} {openProject} />
    </div>
  </section>

  <!-- Popover Section (Modal) -->
  {#if selectedProject}
    <!-- svelte-ignore a11y_click_events_have_key_events -->
    <!-- svelte-ignore a11y_no_noninteractive_tabindex -->
    <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
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
          class="absolute top-0 right-0 mt2 mr2 pa2 bg-near-white br-pill pointer grow"
          onclick={closeProject}
          onkeydown={(e) => e.key === "Enter" && closeProject()}
          aria-label="Close project details"
          tabindex="-1"
        >
          ✕
        </button>

        <h3 id="project-title" class="f4 poppins light-red mb3">
          {selectedProject.name}
        </h3>
        <p class="f6 lh-copy mb3">{selectedProject.description}</p>

        <!-- Links Section -->
        {#each selectedProject.links as link}
          <a
            href={link}
            target="_blank"
            class="f6 link dim br2 ba ph3 pv2 mb2 dib black mr2"
            rel="noopener noreferrer"
          >
            {link}
          </a>
        {/each}
      </div>
    </div>
  {/if}
</main>
