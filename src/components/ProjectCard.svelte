<script>
  export let project;
  export let openProject;
</script>

<div
  class="ma2 br3 w-100 pointer grow"
  onclick={() => openProject(project)}
  onkeydown={(e) => e.key === "Enter" && openProject(project)}
  style="cursor: pointer; transition: transform 0.3s ease;"
  role="button"
  tabindex="0"
  aria-label={`View details of ${project.name}`}
>
  <!-- Image container with fixed height and overflow hidden -->
  <div class="h5 overflow-hidden br3">
    <img
      src={project.image}
      alt={project.name}
      class="w-100 h-100 object-cover"
      onerror={() => (event.target.src = "/images/profile.jpg")}
    />
  </div>
</div>
