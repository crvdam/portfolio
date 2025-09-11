<script>
  import ProjectCardNew from "./ProjectCardNew.svelte";
  import { projects } from "../projectInfo.js";
</script>

<section class="projects">
  <div class="tileWrapper">
    {#each projects as project}
      <ProjectCardNew {project} />
    {/each}
  </div>
</section>

<style>
  .tileWrapper {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    width: 100%;
    gap: 2rem;
  }

  @media screen and (min-width: 768px) {
    .tileWrapper {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
    }
  }
</style>
