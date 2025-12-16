<script>
  import { projects } from "../projectInfo.js";
  import ProjectTile from "./ProjectTile.svelte";
  import { flip } from "svelte/animate";

  let iterableProjects = $state([...projects]);

  function next() {
    iterableProjects = [...iterableProjects.slice(1), iterableProjects[0]];
  }

  function previous() {
    iterableProjects = [
      iterableProjects[iterableProjects.length - 1],
      ...iterableProjects.slice(0, -1),
    ];
  }

  function getItemClass(index) {
    if (index === 0) return "carousel-item previous";
    if (index === 1) return "carousel-item active";
    if (index === 2) return "carousel-item next";
    if (index === 3) return "carousel-item background";
    return "carousel-item";
  }
</script>

<ul class="carousel">
  {#each iterableProjects as project, index (project.id)}
    <li class={getItemClass(index)} animate:flip>
      <ProjectTile {project} />
    </li>
  {/each}
</ul>
<button onclick={previous} class="carousel-btn previous">&#8249</button>
<button onclick={next} class="carousel-btn next">&#8250;</button>

<style>
  .carousel {
    display: flex;
    justify-content: center;
    margin-top: 2rem;
    position: relative;
  }

  .carousel-btn {
    position: absolute;
    padding: 1rem 0.5rem;
    top: 45%;
    font-size: 4rem;
  }

  .carousel-btn:hover {
    color: var(--clr-primary);
    transition: 0.2s;
  }

  .carousel-btn.previous {
    left: 0;
  }

  .carousel-btn.next {
    right: 0;
  }

  .carousel-item {
    position: absolute;
    top: 0;
    z-index: -2;
    display: none;
  }

  .carousel-item.active {
    z-index: 1;
    display: block;
  }

  .carousel-item.previous,
  .carousel-item.next {
    filter: brightness(0.2);
    z-index: -1;
  }

  .carousel-item.previous {
    transform: scale(0.95) translate(-250px, -30px);
  }

  .carousel-item.next {
    transform: scale(0.95) translate(250px, -30px);
  }

  .carousel-item.background {
    transform: scale(0.85) translate(0, -100px);
    filter: brightness(0.1);
    z-index: -3;
  }

  @media screen and (min-width: 1024px) {
    .carousel {
      display: flex;
      justify-content: center;
    }

    .carousel-item {
      position: absolute;
      top: 0;
      z-index: -2;
      display: block;
    }
  }
</style>
