<script>
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let { title, imageName, description, github, web, stack } = $props();
</script>

<div class="tile">
  <div class="tile__image">
    <img src={`/${imageName}`} alt={`${title} Project`} />
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
    width: 22rem;
    height: 25rem;
    position: relative;
    transition:
      transform 0.5s,
      box-shadow 0.4s;
  }

  .tile:hover {
    transform: translate(5px, -10px) scale(1.03);
    box-shadow: -5px 10px 5px rgba(0, 0, 0, 0.6);
    z-index: 10;
    opacity: 1;
    filter: brightness(100%);
  }

  .tile__image {
    height: 100%;
    width: 100%;
    position: absolute;
    filter: brightness(30%);
    transition: filter 0.5s;

    img {
    }
  }

  .tile:hover .tile__image {
    filter: brightness(100%);
  }

  .tile__title {
    color: var(--background-clr-card);
    font-size: 1.2rem;
    font-weight: 700;
    letter-spacing: 1px;
    bottom: 3rem;
    left: 1.5rem;
    transition: bottom 0.5s ease-out;
    position: absolute;
  }

  .tile:hover .tile__title {
    bottom: 10rem;
    transition: bottom 0.5s ease-out;
  }

  .tile__infoBackground {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: rgba(0, 0, 0, 0.7);
    padding: 1rem;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 5rem;
    transform: scaleY(1);
    transition: transform 0.7s ease-out;
    transform-origin: bottom;
  }

  .tile:hover .tile__infoBackground {
    transform: scaleY(2.5);
    transition: transform 0.5s ease-out;
  }

  .tile__infoDetails {
    position: absolute;
    transform: scaleY(0);
    transition: transform 0.5s ease-out;
    transform-origin: bottom;
    bottom: 1rem;
    left: 1rem;
  }

  .tile:hover .tile__infoDetails {
    transform: scaleY(1);
    transition: transform 0.5s ease-out;
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

  .tile__icon:hover {
    filter: grayscale(100%) brightness(200%);
    margin-right: 0.5rem;
    transform: scale(1.2);
    transition: transform 0.2s ease-out;
  }

  .tile__icon:active {
    transform: scale(0.9);
  }
</style>
