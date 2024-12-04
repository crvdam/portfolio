<script>
  import me from "/me.jpg?url";
  import githubIcon from "/ic-github.png?url";
  import linkedinIcon from "/ic-linkedin.png?url";
</script>

<div class="hero">
  <div class="hero__text">
    <h1>Caspar van Dam</h1>
    <h3>Web developer based in Amsterdam, The Netherlands</h3>
    <h2>About</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo
      necessitatibus architecto officiis autem aliquam, saepe, temporibus ea
      minima ad laudantium accusantium iure ex. Amet voluptatibus ad soluta id
      doloremque! Tempore.
    </p>
  </div>
  <div class="hero__image">
    <img src={me} alt="This is me." />
  </div>
  <div class="hero__socials">
    <a href="https://github.com/crvdam">
      <img src={githubIcon} alt="Github" />
    </a>
    <a href="https://linkedin.com/in/casparvandam">
      <img src={linkedinIcon} alt="LinkedIn" />
    </a>
  </div>
</div>

<style>
  .hero {
    background-color: var(--background-clr-hero);
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    padding: 2rem 2.5rem 0 2.5rem;
  }

  .hero__text {
    text-align: center;
    order: 1;
    margin-bottom: 2rem;
  }

  h1 {
    color: var(--text-clr-primary);
    font-weight: 700;
    margin-bottom: 0.5rem;
  }

  h2 {
    color: var(--text-clr-secondary);
  }

  h3 {
    color: var(--text-clr-tertiary);
    margin-bottom: 2rem;
  }

  p {
    color: var(--text-clr-tertiary);
  }

  .hero__image {
    order: 0;
  }

  .hero__image > img {
    width: 15rem;
    height: 15rem;
    border-radius: 50%;
    object-fit: cover;
  }

  .hero__socials {
    order: 2;
  }

  .hero__socials > a {
    margin: 0 0.25em;
  }

  .hero__socials > a > img {
    height: 2.5rem;
    width: 2.5rem;
  }
</style>
