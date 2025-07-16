<script>
  import ProjectCard from "./ProjectCard.svelte";
  import ProjectCardNew from "./ProjectCardNew.svelte";
  import { projects } from "../lib/projectInfo.js";
</script>

<section class="projects">
  <div class="projects__header">
    <h2>A selection of my personal projects</h2>
  </div>
  <div class="project-cards-wrapper">
    {#each projects as project}
      <ProjectCard
        title={project.title}
        imageName={project.imageName}
        description={project.description}
        github={project.github}
        web={project.web}
        stack={project.stack}
      />
    {/each}

    <!-- {#each projects as project}
      <ProjectCardNew
        title={project.title}
        imageName={project.imageName}
        description={project.description}
        github={project.github}
        web={project.web}
        stack={project.stack}
      />
    {/each} -->
  </div>
</section>

<style>
  .projects {
    background-color: var(--background-clr-projects);
    color: var(--background-clr-hero);
    padding: 3rem 0;
    margin: auto;
  }

  .project-cards-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto;
    gap: 2rem;
    max-width: 1400px;
  }

  .projects__header {
    margin-bottom: 2rem;
    text-align: center;
  }

  @media (min-width: 768px) {
    .project-cards-wrapper {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      margin: auto;
    }
  }
</style>
