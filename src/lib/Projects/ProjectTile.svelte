<script>
  import { onMount } from "svelte";
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  const { project } = $props();

  let isDesktop = $state(false);

  onMount(() => {
    isDesktop = window.innerWidth >= 1024;

    const handleResize = () => {
      isDesktop = window.innerWidth >= 1024;
    };

    window.addEventListener("resize", handleResize);
  });
</script>

<div class="project-tile">
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
        <img src={`/${project.imageName}`} alt={`${project.title} Project`} />
      {:else}
        <img
          src={`/project-placeholder.webp`}
          alt={`${project.title} Project`}
        />
      {/if}
    </div>
  </div>

  <div class="info">
    <h2 class="title">{project.title}</h2>

    <div class="description">
      {#if project.description}
        <p>{project.description}</p>
      {/if}
    </div>

    <div class="stack-links-container">
      <ul class="stack-wrapper">
        {#each project.stack as stackItem}
          <li class="stack-item">{stackItem}</li>
        {/each}
      </ul>

      <div class="links-wrapper">
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
    </div>
  </div>
</div>

<style>
  .project-tile {
    background: var(--bg-tile);
    color: var(--clr-tile);
    border-radius: 8px;
    margin: auto;
    height: 500px;
  }

  .project-video {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    opacity: 0;
  }

  .info {
    display: flex;
    flex-direction: column;
    height: 250px;
    padding: 1rem;
  }

  .title {
    margin-bottom: 0.5rem;
  }

  .media-wrapper img,
  .media-wrapper video {
    height: 250px;
    border-radius: 8px 8px 0 0;
    margin-bottom: auto;
  }

  .media-wrapper img {
    object-fit: cover;
    margin-bottom: auto;
  }

  .stack-links-container {
    margin-top: auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .stack-wrapper {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .stack-item {
    border: 1px solid black;
    padding: 0.2rem 0.5rem;
    border-radius: 8px;
    font-size: 0.8rem;
  }

  .description {
    margin-bottom: 2rem;
  }

  .links-wrapper {
    display: flex;
    justify-content: right;
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

  @media (hover: hover) and (pointer: fine) {
    .project-tile:hover .project-video {
      opacity: 1;
      transition: 0.2s;
    }

    .icon:hover {
      filter: brightness(0);
      transition: 0.2s;
    }
  }

  @media screen and (min-width: 1024px) {
    .project-tile {
      width: 400px;
    }
  }
</style>
