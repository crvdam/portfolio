<script>
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let { title, imageName, text, github, web, tech } = $props();
</script>

<div class="card">
  <div class="card__image">
    <img src={`/${imageName}`} alt="Project screenshot" />
  </div>

  <h2 class="card__title">{title}</h2>

  <div class="card__seperator"></div>

  <p class="card__text">
    {text}
  </p>

  <div class="card__tech">
    {#each tech as item}
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
    background-color: var(--background-clr-card);
    color: var(--background-clr-hero);
    border: 1px solid var(--text-clr-quaternary);
    border-radius: 5%;
    padding: 1rem;
    margin: 0.5rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .card__image {
    width: 100%;
    height: 12rem;
  }

  .card__image > img {
    border-radius: 5%;
    width: 100%;
    height: 100%;
    object-fit: fill;
  }

  .card__title {
    text-align: left;
  }

  .card__seperator {
    height: 2px;
    width: 40%;
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
    font-size: 0.6rem;
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
    height: 2.5rem;
    margin-right: 0.5rem;
    transform: scale(1.1);
    transition: 0.2s ease-out;
  }

  .card__links__icon:active {
    transform: scale(0.9);
  }
</style>
