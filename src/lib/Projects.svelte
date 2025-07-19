<script>
  import ProjectCard from "./ProjectCard.svelte";
  import ProjectCardNew from "./ProjectCardNew.svelte";
  import { projects } from "../lib/projectInfo.js";
</script>

<section class="projects">
  <div class="projects__header">
    <h2>A selection of my personal projects</h2>
  </div>
  <div class="projects__tileWrapper">
    {#each projects as project, index}
      <ProjectCardNew
        title={project.title}
        imageName={project.imageName}
        videoName={project.videoName}
        description={project.description}
        github={project.github}
        web={project.web}
        stack={project.stack}
        {index}
      />
    {/each}
  </div>
</section>

<style>
  .projects {
    background: linear-gradient(
      90deg,
      var(--background-clr-projects1) 0%,
      var(--background-clr-projects2) 30%,
      var(--background-clr-projects2) 70%,
      var(--background-clr-projects3) 100%
    );
    color: var(--background-clr-hero);
    padding: 10rem 0;
    margin: auto;
  }

  .projects__tileWrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto;
    gap: 4rem;
    max-width: 1400px;
  }

  .projects__header {
    font-size: 2rem;
    margin-bottom: 6rem;
    text-align: center;
  }

  @media (min-width: 768px) {
    .projects {
      padding: 10rem 0;
    }

    .projects__tileWrapper {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      margin: auto;
      gap: 4rem;
    }

    .projects__header {
      margin-bottom: 6rem;
      text-align: center;
    }

    .projects__tileWrapper:nth-child(1) {
      transform: scale(20);
    }
  }
</style>
