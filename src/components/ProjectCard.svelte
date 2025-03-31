<script>
  export let project;
  export let openProject;
</script>

<div
  class="ba ma3 br3 w-40-l w-60-m w-100 pointer grow"
  onclick={() => openProject(project)}
  onkeydown={(e) => e.key === "Enter" && openProject(project)}
  style="cursor: pointer; transition: transform 0.3s ease;"
  role="button"
  tabindex="0"
  aria-label={`View details of ${project.name}`}
>
  <img
    src={project.image}
    alt={project.name}
    class="w-100 h-100 br3 object-cover"
    onerror={() => (event.target.src = "/images/profile.jpg")}
  />
</div>
