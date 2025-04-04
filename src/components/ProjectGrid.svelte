<script>
  import ProjectCard from "./ProjectCard.svelte";

  export let projects = [];
  export let openProject;
</script>

<div class="flex flex-row-l flex-row-m flex-column-ns justify-center">
  {#each projects as project (project.id)}
    <div class="w-100-l w-80-m w-80-ns pa2">
      <ProjectCard {project} {openProject} />
    </div>
  {/each}
</div>
