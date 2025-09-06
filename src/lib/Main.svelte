<script>
  import About from "./About.svelte";
  import Projects from "./Projects/Projects.svelte";
  import Contact from "./Contact.svelte";
  import { fade } from "svelte/transition";

  export let activePage;
  let animate = false;
  let triggeredOnce = true;
  let animationDelay = 0;

  $: if (activePage && !triggeredOnce) {
    animate = true;
    triggeredOnce = true;

    setTimeout(() => {
      animationDelay = 0;
    }, 2000);
  }
</script>

<main class:animate-once={animate}>
  {#if activePage === "about"}
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <About />
    </section>
  {:else if activePage === "projects"}
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <Projects />
    </section>
  {:else if activePage === "contact"}
    <section in:fade={{ duration: 500, delay: animationDelay }}>
      <Contact />
    </section>
  {/if}
</main>

<style>
  main {
    display: flex;
    align-items: center;
    margin-left: auto;
    margin-right: auto;
    height: 100%;
  }

  section {
    margin: auto;
  }

  @media screen and (min-width: 1280px) {
    main {
      height: 70%;
      width: 70%;
    }

    .animate-once {
      animation: mainAppear 1s ease forwards;
    }

    @keyframes mainAppear {
      0% {
        box-shadow: 0px 0px 0px rgba(0, 0, 0, 0);
        background-color: rgba(0, 0, 0, 0);
        backdrop-filter: blur(0);
      }

      100% {
        box-shadow: 0px 0px 10px 15px rgba(20, 20, 50, 0.3);
        background-color: rgba(20, 20, 50, 0.3);
        backdrop-filter: blur(15px);
      }
    }
  }
</style>
