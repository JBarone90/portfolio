<script>
  import ProjectCard from "./ProjectCard.svelte";

  export let projects = [];
  export let openProject;
</script>

<div class="flex flex-wrap justify-center">
  {#each projects as project (project.id)}
    <ProjectCard {project} {openProject} />
  {/each}
</div>
