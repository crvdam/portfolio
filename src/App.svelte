<script>
  import Hero from "./lib/Hero.svelte";
  import Projects from "./lib/Projects.svelte";
  import AboutMe from "./lib/AboutMe.svelte";
  import Footer from "./lib/Footer.svelte";
</script>

<main>
  <Hero />

  <section>
    <div class="dividerTop">
      <svg
        data-name="Layer 1"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 1200 120"
        preserveAspectRatio="none"
      >
        <path
          d="M600,112.77C268.63,112.77,0,65.52,0,7.23V120H1200V7.23C1200,65.52,931.37,112.77,600,112.77Z"
          class="shape-fill"
        ></path>
      </svg>
    </div>
  </section>

  <Projects />

  <section>
    <div class="dividerBottom">
      <svg
        data-name="Layer 1"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 1200 120"
        preserveAspectRatio="none"
      >
        <path
          d="M600,112.77C268.63,112.77,0,65.52,0,7.23V120H1200V7.23C1200,65.52,931.37,112.77,600,112.77Z"
          class="shape-fill"
        ></path>
      </svg>
    </div>
  </section>

  <AboutMe />
</main>

<Footer />

<style>
  section {
    position: relative;
  }

  .dividerTop {
    position: absolute;
    top: -2px;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
    transform: rotate(180deg);
  }

  .dividerTop svg {
    position: relative;
    display: block;
    width: 100%;
    height: 150px;
  }

  .dividerTop .shape-fill {
    fill: var(--background-clr-hero);
  }

  .dividerBottom {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
    bottom: -2px;
  }

  .dividerBottom svg {
    position: relative;
    display: block;
    width: calc(100% + 1.3px);
    height: 150px;
  }

  .dividerBottom .shape-fill {
    fill: var(--background-clr-hero);
  }
</style>
