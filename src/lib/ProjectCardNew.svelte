<script>
  import githubIcon from "/ic-github-dark.png?url";
  import internetIcon from "/ic-internet-dark.png?url";

  let { title, imageName, description, github, web, stack } = $props();
</script>

<div class="tile">
  <div class="tile__image">
    <img src={`/${imageName}`} alt={`${title} Project`} />
  </div>

  <h4 class="tile__title">{title}</h4>

  <div class="tile__infoContainer">
    <p>{description}</p>
    <ul>
      {#each stack as stackItem}
        <li>{stackItem}</li>
      {/each}
    </ul>
  </div>
</div>

<style>
  .tile {
    width: 22rem;
    height: 25rem;
    position: relative;
    border-radius: 5px;
    transition:
      transform 0.5s,
      box-shadow 0.4s;
  }

  .tile__image {
    height: 100%;
    width: 100%;
    position: absolute;
    filter: brightness(40%);
    transition: filter 0.5s;

    img {
      border-radius: 5px;
    }
  }

  .tile__title {
    color: white;
    position: absolute;
    font-size: 1.2rem;
    font-weight: 700;
    letter-spacing: 1px;
    bottom: 3rem;
    left: 2.5rem;
    transition: transform 0.5s;
  }

  .tile__infoContainer {
    background-color: red;
    border-radius: 5px;
    position: absolute;
    bottom: 1rem;
    left: 1rem;
    right: 1rem;
  }

  .tile:hover .tile__title {
    transform: translateY(-15rem);
  }

  .tile:hover {
    transform: translate(5px, -10px) scale(1.03);
    box-shadow: -5px 10px 5px rgba(0, 0, 0, 0.6);
    z-index: 10;
    opacity: 1;
    filter: brightness(100%);
  }

  .tile:hover .tile__infoContainer {
    transform: translate(5px, -10px) scale(1.03);
    z-index: 20;
  }
</style>
