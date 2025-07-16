<script>
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let { title, imageName, description, github, web, stack } = $props();
</script>

<div class="card">
  <div class="card__image">
    <img src={`/${imageName}`} alt="Project screenshot" />
  </div>

  <h2 class="card__title">{title}</h2>

  <div class="card__seperator"></div>

  <p class="card__text">
    {description}
  </p>

  <div class="card__tech">
    {#each stack as item}
      <span class="card__tech__bubble">{item}</span>
    {/each}
  </div>

  <div class="card__links">
    {#if github}
      <a href={github}>
        <img class="card__links__icon" src={githubIcon} alt="Github link" />
      </a>
    {/if}
    {#if web}
      <a href={web}>
        <img class="card__links__icon" src={internetIcon} alt="LinkedIn link" />
      </a>
    {/if}
  </div>
</div>

<style>
  .card {
    width: 20rem;
    height: 35rem;
    background-color: var(--background-clr-card);
    color: var(--background-clr-hero);
    border: 1px solid var(--text-clr-quaternary);
    border-radius: 5%;
    padding: 1.5rem;
    margin: 0.5rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .card__image {
    width: 100%;
    height: 12rem;
    margin-bottom: 1rem;
  }

  .card__image > img {
    border-radius: 5%;
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  .card__title {
    text-align: left;
  }

  .card__seperator {
    height: 1px;
    width: 70px;
    background-color: var(--text-clr-primary);
  }

  .card__text {
    text-align: left;
  }

  .card__tech {
    text-align: left;
    display: flex;
    flex-wrap: wrap;
    gap: 0.3rem;
  }

  .card__tech__bubble {
    font-size: 0.8rem;
    background-color: var(--background-clr-projects);
    color: var(--background-clr-hero);
    border: 1px solid var(--text-clr-quaternary);
    border-radius: 5%;
    padding: 0.5rem;
  }

  .card__links {
    text-align: left;
    flex-grow: 1;
    display: flex;
    align-items: flex-end;
  }

  .card__links__icon {
    height: 2.5rem;
    margin-right: 0.5rem;
  }

  .card__links__icon:hover {
    filter: invert(7%) sepia(11%) saturate(3319%) hue-rotate(190deg)
      brightness(30%) contrast(109%);
    height: 2.5rem;
    margin-right: 0.5rem;
    transform: scale(1.1);
    transition: transform 0.2s ease-out;
  }

  .card__links__icon:active {
    transform: scale(0.9);
  }
</style>
