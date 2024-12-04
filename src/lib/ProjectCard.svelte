<script>
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let { title, imageName, text, github, web } = $props();
</script>

<div class="card">
  <img class="card__image" src={`"/${imageName}`} alt="Project screenshot" />
  <h2>{title}</h2>
  <div class="card__seperator"></div>
  <p>
    {text}
  </p>
  <div class="card__links">
    <a href={github}>
      <img class="links__icon" src={githubIcon} alt="Github link" />
    </a>
    <a href={web}>
      <img class="links__icon" src={internetIcon} alt="LinkedIn link" />
    </a>
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
  }

  .card__seperator {
    height: 2px;
    width: 50%;
    background-color: var(--text-clr-primary);
    margin-top: 0.5rem;
    margin-bottom: 1rem;
  }

  p {
    margin-bottom: 1.5rem;
  }

  .card > h2,
  p {
    text-align: left;
  }

  .card__image {
    width: 100%;
    border-radius: 5%;
    margin-bottom: 1.5rem;
    object-fit: contain;
  }

  .card__links {
    text-align: left;
  }

  .links__icon {
    height: 2.5rem;
    margin-right: 0.5rem;
  }
</style>
