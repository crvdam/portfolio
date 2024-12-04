<script>
  import ProjectCard from "./ProjectCard.svelte";
  import { projects } from "../lib/projectInfo.js";
</script>

<div class="projects">
  <h1>Projects</h1>
  {#each projects as project}
    <ProjectCard
      title={project.title}
      imageName={project.imageName}
      text={project.text}
      github={project.github}
      web={project.web}
    />
  {/each}
</div>

<style>
  .projects {
    background-color: var(--background-clr-projects);
    color: var(--background-clr-hero);
    padding: 3rem 3rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    text-align: center;
  }
</style>
