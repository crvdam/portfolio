<script>
  import { onMount } from "svelte";
  import { projects } from "../projectInfo.js";
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let isDesktop = $state(false);

  onMount(() => {
    isDesktop = window.innerWidth >= 1024;

    const handleResize = () => {
      isDesktop = window.innerWidth >= 1024;
    };

    window.addEventListener("resize", handleResize);
  });
</script>

<h2 class="intro-text">
  This is a selection of the projects I've used to explore new languages,
  frameworks and libraries.
</h2>

<ul class="project-list">
  {#each projects as project, index (project.id)}
    <li class="project-item {project.id % 2 === 0 ? 'reverse' : ''}">
      <div class="project-info-wrapper">
        <h3>{project.title}</h3>
        <p>{project.description}</p>

        <ul class="feature-list">
          {#each project.features as feature, index}
            {#if index === 0}
              <li>{feature}</li>
            {:else}
              <span>|</span>
              <li>{feature}</li>
            {/if}
          {/each}
        </ul>

        <ul class="stack-list">
          {#each project.stack as stackItem}
            <li class="stack-item">{stackItem}</li>
          {/each}
        </ul>

        {#if project.github}
          <a
            target="_blank"
            rel="noopener noreferrer"
            class="icon"
            href={project.github}
            aria-label="Github link"
          >
            <img src={githubIcon} alt="Github link" />
          </a>
        {/if}

        {#if project.web}
          <a class="icon" href={project.web} aria-label="Project link">
            <img src={internetIcon} alt="Project link" />
          </a>
        {/if}
      </div>

      <div class="media-wrapper">
        {#if isDesktop && project.videoName}
          <div class="project-video">
            <video autoplay muted loop>
              <source src={`/${project.videoName}`} />
            </video>
          </div>
        {/if}

        <div class="project-image">
          {#if project.imageName}
            <img
              src={`/${project.imageName}`}
              alt={`${project.title} Project`}
            />
          {:else}
            <img
              src={`/project-placeholder.webp`}
              alt={`${project.title} Project`}
            />
          {/if}
        </div>
      </div>
    </li>
  {/each}
</ul>

<style>
  .intro-text {
    margin-bottom: 4rem;
  }

  .project-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
  }

  .project-item {
    width: 100%;
    display: flex;
    flex-direction: column;
    padding: 2rem;
    gap: 1rem;
    background-color: var(--clr-secondary);
    border-radius: 20px;
  }

  .project-info-wrapper {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  h3 {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  h2 {
    font-size: 1.5rem;
    font-weight: 600;
  }

  .feature-list {
    flex-grow: 1;
    margin-top: 1rem;
    margin-bottom: 2rem;
  }

  .feature-list li {
    display: inline-block;
    font-weight: 700;
  }

  .feature-list span {
    margin: 0 0.5rem;
  }

  .stack-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-bottom: 1rem;
  }

  .stack-item {
    font-weight: 700;
    padding: 0.25rem 0.5rem;
    background-color: var(--clr-main);
    color: var(--bg-main);
    border-radius: 2px;
  }

  .icon {
    display: block;
    height: 48px;
    width: 48px;
  }

  img {
    height: 100%;
    width: 100%;
  }

  .project-video {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    opacity: 0;
  }

  .media-wrapper {
    position: relative;
    height: 250px;
    aspect-ratio: 16 / 9;
  }

  .media-wrapper img,
  .media-wrapper video {
    height: 250px;
    border-radius: 20px;
    margin-bottom: auto;
  }

  .media-wrapper img {
    object-fit: cover;
    margin-bottom: auto;
  }

  @media (hover: hover) and (pointer: fine) {
    .project-item:hover .project-video {
      opacity: 1;
      transition: 0.2s;
    }

    .icon:hover {
      filter: brightness(0) invert(1);
      transition: 0.2s;
    }
  }

  @media screen and (min-width: 1024px) {
    .project-item {
      flex-direction: row;
      text-align: left;
    }

    .reverse {
      flex-direction: row-reverse;

      .project-info-wrapper {
        align-items: flex-end;
        text-align: right;
      }
    }

    .media-wrapper {
      max-width: 40%;
    }

    .feature-list {
      margin-bottom: 0;
    }
  }
</style>
