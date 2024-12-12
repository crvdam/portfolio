<script>
  import ProjectCard from "./ProjectCard.svelte";
  import { projects } from "../lib/projectInfo.js";
</script>

<div class="projects">
  <h1 class="projects__header">Projects</h1>
  <div class="project-cards-wrapper">
    {#each projects as project}
      <ProjectCard
        title={project.title}
        imageName={project.imageName}
        text={project.text}
        github={project.github}
        web={project.web}
        tech={project.tech}
      />
    {/each}
  </div>
</div>

<style>
  .projects {
    background-color: var(--background-clr-projects);
    color: var(--background-clr-hero);
    display: grid;
    justify-content: center;
    text-align: center;
    padding: 3rem 0;
    margin: auto;
  }

  .projects__header {
    margin-bottom: 2rem;
  }

  @media (min-width: 768px) {
    .project-cards-wrapper {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin: auto;
    }
  }
</style>
