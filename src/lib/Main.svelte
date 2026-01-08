<script>
  import About from "./About.svelte";
  import ProjectCarousel from "./Projects/ProjectCarousel.svelte";
  import ProjectList from "./Projects/ProjectList.svelte";
  import Contact from "./Contact.svelte";
  import { fade } from "svelte/transition";
  import Portfolio from "./Portfolio.svelte";
  import { onMount } from "svelte";

  export let activePage;
  export let goToPage;

  let animationDelay = 0;
  let animate = false;

  onMount(() => {
    setTimeout(() => {
      animate = true;
    }, 2800);
  });
</script>

<main class:animate-once={animate}>
  {#if activePage === "about"}
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <About {goToPage} />
    </section>
  {:else if activePage === "projects"}
    <!-- <section in:fade={{ duration: 500, delay: animationDelay }}>
      <ProjectCarousel />
    </section> -->
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <ProjectList />
    </section>
  {:else if activePage === "contact"}
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <Contact />
    </section>
  {:else if activePage === "portfolio"}
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <Portfolio />
    </section>
  {/if}
</main>

<style>
  main {
    opacity: 0;
    padding: 2rem 1rem 0;
    max-width: 1200px;
    margin: 120px auto 0;
    background: var(--bg-main);
    min-height: calc(100vh - 173px);
    transform: translateY(10px);
  }

  .animate-once {
    animation: fadeIn 1.5s ease forwards;
  }

  @media screen and (min-width: 768px) {
    main {
      padding: 2rem;
      margin-top: 0;
    }
  }

</style>
