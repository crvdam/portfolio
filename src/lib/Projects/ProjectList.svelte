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

<div class="intro-text">
  <h1>Personal Projects</h1>

  <p>
    These projects reflect my approach to learning through building. Every new
    project is an exercise, designed to introduce me to a new concept,
    framework, or language. At the moment, I’m focusing on Next.js, with plans
    to explore back-end development using C# and .NET Core next. I’ll continue
    to update this page as projects are completed.
  </p>
</div>

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
              ,
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
    margin-left: 1rem;

    p {
      margin-bottom: 1rem;
    }
  }

  .project-list {
    margin-top: 2rem;
  }

  .project-item {
    display: flex;
    flex-direction: column;
    padding: 2rem 1rem;
    gap: 2rem;
    background-color: var(--bg-tile);
    border-radius: 20px;
    margin-bottom: 1rem;
  }

  .project-info-wrapper {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  h3 {
    font-size: 1.5rem;
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
    font-weight: 400;
  }

  .stack-list {
    display: flex;
    flex-wrap: wrap;
    font-size: 14px;
    gap: 0.5rem;
    margin-bottom: 1rem;
  }

  .stack-item {
    font-weight: 400;
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

  .project-image {
    overflow: hidden;
    width: 100%;
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
    height: 200px;
  }

  .media-wrapper img,
  .media-wrapper video {
    height: 200px;
    width: 280px;
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
    .intro-text {
      width: 70%;
    }

    .project-item {
      flex-direction: row;
      text-align: left;
      padding: 2rem;
    }

    .reverse {
      flex-direction: row-reverse;

      .project-info-wrapper {
        align-items: flex-end;
        text-align: right;
      }
    }

    .media-wrapper {
      width: 280px;
    }

    .feature-list {
      margin-bottom: 0;
    }

    .media-wrapper img,
    .media-wrapper video {
      height: 200px;
      width: 100%;
    }
  }
</style>
