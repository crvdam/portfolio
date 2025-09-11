<script>
  import { onMount } from "svelte";
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  const { project } = $props();

  let isDesktop = $state(false);

  onMount(() => {
    isDesktop = window.innerWidth >= 1000;

    const handleResize = () => {
      isDesktop = window.innerWidth >= 1000;
    };

    window.addEventListener("resize", handleResize);
  });
</script>

<div class="tile">
  <div class="tile__media">
    {#if isDesktop && project.videoName}
      <div class="tile__video">
        <video autoplay muted loop>
          <source src={`/${project.videoName}`} />
        </video>
      </div>
    {/if}

    <div class="tile__image">
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

  <div class="tile__infoBackground"></div>

  <h4 class="tile__title">{project.title}</h4>
  <div class="tile__infoDetails">
    <ul class="tile__list">
      {#each project.stack as stackItem}
        <li class="tile__stackItem">{stackItem}</li>
      {/each}
    </ul>

    <div class="tile_list">
      {#if project.github}
        <a
          target="_blank"
          rel="noopener noreferrer"
          class="icon"
          href={project.github}
        >
          <img src={githubIcon} alt="Github link" />
        </a>
      {/if}

      {#if project.web}
        <a class="icon" href={project.web}>
          <img src={internetIcon} alt="Project link" />
        </a>
      {/if}
    </div>
  </div>
</div>

<style>
  .tile {
    height: 200px;
    width: 280px;
    position: relative;
    transition:
      transform 0.5s,
      box-shadow 0.4s;
  }

  .tile__media {
    height: 100%;
    width: 100%;
    position: absolute;
  }

  .tile__image,
  .tile__video {
    width: 100%;
    height: 100%;
    border-radius: 7px;
  }

  img,
  video {
    border-radius: 7px;
  }

  .tile__video {
    display: none;
  }

  .tile__title {
    color: var(--background-clr-card);
    font-weight: 500;
    letter-spacing: 1px;
    bottom: 2.5rem;
    left: 1rem;
    position: absolute;
  }

  .tile__infoBackground {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: var(--background);
    border-bottom-left-radius: 7px;
    border-bottom-right-radius: 7px;
    padding: 1rem;
    position: absolute;
    bottom: -1px;
    left: 0;
    right: 0;
    height: 4.5rem;
  }

  .tile__infoDetails {
    width: 100%;
    display: flex;
    justify-content: space-between;
    position: absolute;
    bottom: 0.5rem;
    padding: 0 1rem;
  }

  .tile__list {
    display: flex;
    align-items: flex-end;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .tile__stackItem {
    padding: 5px;
    border-radius: 5px;
    font-size: 0.7rem;
    font-weight: 600;
  }

  .icon img {
    height: 35px;
    width: 35px;
  }

  @media screen and (min-width: 641px) {
    .tile {
      width: 280px;
      height: 200px;
    }
  }

  @media screen and (min-width: 1280px) {
    .tile:hover {
      transform: translateY(-10px) scale(1);
      z-index: 10;
      opacity: 1;
      filter: brightness(100%);
    }

    .tile__media {
      filter: brightness(100%);
      transition: filter 0.5s;
      position: relative;
    }

    .tile:hover .tile__media {
      filter: brightness(100%);
    }

    .tile:hover .tile__media:has(video) {
      .tile__video {
        display: block;
      }

      .tile__image {
        display: none;
      }
    }

    .tile__title {
      bottom: 1rem;
      transition: bottom 0.3s ease-out;
    }

    .tile:hover .tile__title {
      bottom: 3rem;
      transition: bottom 0.5s ease-out;
    }

    .tile__infoBackground {
      transform-origin: bottom;
      border-bottom-left-radius: 3px;
      border-bottom-right-radius: 3px;
      height: 3rem;
      transition: transform 0.3s ease-out;
    }

    .tile:hover .tile__infoBackground {
      transition: transform 0.5s ease-out;
      transform: scaleY(1.7);
    }

    .tile__infoDetails {
      opacity: 0;
    }

    .tile:hover .tile__infoDetails {
      opacity: 1;
      transition: opacity 0.1s ease-out;
      transition-delay: 0.3s;
    }
  }
</style>
