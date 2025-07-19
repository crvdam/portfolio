<script>
  import { onMount } from "svelte";
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let { title, imageName, videoName, description, github, web, stack } =
    $props();

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
    {#if isDesktop && videoName}
      <div class="tile__video">
        <video autoplay muted loop>
          <source src={`/${videoName}`} />
        </video>
      </div>
    {/if}

    <div class="tile__image">
      {#if imageName}
        <img src={`/${imageName}`} alt={`${title} Project`} />
      {:else}
        <img src={`/project-placeholder.webp`} alt={`${title} Project`} />
      {/if}
    </div>
  </div>

  <div class="tile__infoBackground"></div>

  <h4 class="tile__title">{title}</h4>
  <div class="tile__infoDetails">
    <ul class="tile__list">
      {#each stack as stackItem}
        <li class="tile__stackItem">{stackItem}</li>
      {/each}
    </ul>

    <div class="tile_list">
      {#if github}
        <a href={github}>
          <img class="tile__icon" src={githubIcon} alt="Github link" />
        </a>
      {/if}

      {#if web}
        <a href={web}>
          <img class="tile__icon" src={internetIcon} alt="Project link" />
        </a>
      {/if}
    </div>
  </div>
</div>

<style>
  .tile {
    width: 400px;
    height: 300px;
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
  }

  .tile__video video,
  .tile__image img {
    width: 100%;
    height: 100%;
    object-fit: fill;
  }

  .tile__video {
    display: none;
  }

  .tile__title {
    color: var(--background-clr-card);
    font-size: 1.2rem;
    font-weight: 700;
    letter-spacing: 1px;
    bottom: 8rem;
    left: 1rem;
    position: absolute;
  }

  .tile__infoBackground {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: rgba(0, 0, 0, 0.8);
    padding: 1rem;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 10.5rem;
  }

  .tile__infoDetails {
    position: absolute;
    bottom: 1rem;
    left: 1rem;
  }

  .tile__list {
    display: flex;
    list-style: none;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-bottom: 1rem;
  }

  .tile__stackItem {
    padding: 5px;
    background-color: var(--background-clr-projects1);
    color: var(--background-clr-hero);
    border-radius: 5px;
    font-size: 0.7rem;
    font-weight: 600;
  }

  .tile__icon {
    height: 3rem;
    width: 3rem;
    margin-right: 0.5rem;
  }

  @media screen and (min-width: 1280px) {
    .tile:hover {
      transform: translate(5px, -10px) scale(1.2);
      box-shadow: -5px 10px 5px rgba(0, 0, 0, 0.6);
      z-index: 10;
      opacity: 1;
      filter: brightness(100%);
    }

    .tile__media {
      filter: brightness(30%);
      transition: filter 0.5s;
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
      transition: bottom 0.5s ease-out;
    }

    .tile:hover .tile__title {
      bottom: 8rem;
      transition: bottom 0.5s ease-out;
    }

    .tile__infoBackground {
      transition: transform 0.7s ease-out;
      transform-origin: bottom;
      height: 3rem;
    }

    .tile:hover .tile__infoBackground {
      transform: scaleY(3.3);
      transition: transform 0.5s ease-out;
    }

    .tile__infoDetails {
      transform: scaleY(0);
      transition: transform 0.5s ease-out;
      transform-origin: bottom;
    }

    .tile:hover .tile__infoDetails {
      transform: scaleY(1);
      transition: transform 0.5s ease-out;
    }

    .tile__icon:hover {
      filter: grayscale(100%) brightness(200%);
      margin-right: 0.5rem;
      transform: scale(1.2);
      transition: transform 0.2s ease-out;
    }

    .tile__icon:active {
      transform: scale(0.9);
    }
  }
</style>
