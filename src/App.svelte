<script>
  import Hero from "./lib/Hero.svelte";
  import Projects from "./lib/Projects.svelte";
  import Footer from "./lib/Footer.svelte";
</script>

<main>
  <Hero />

  <section>
    <div class="custom-shape-divider-top-1733308504">
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
    <div class="custom-shape-divider-bottom-1733316495">
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
</main>

<Footer />

<style>
  section {
    position: relative;
  }

  .custom-shape-divider-top-1733308504 {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
    transform: rotate(180deg);
  }

  .custom-shape-divider-top-1733308504 svg {
    position: relative;
    display: block;
    width: 100%;
    height: 20px;
  }

  .custom-shape-divider-top-1733308504 .shape-fill {
    fill: var(--background-clr-hero);
  }

  .custom-shape-divider-bottom-1733316495 {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
  }

  .custom-shape-divider-bottom-1733316495 svg {
    position: relative;
    display: block;
    width: calc(100% + 1.3px);
    height: 20px;
  }

  .custom-shape-divider-bottom-1733316495 .shape-fill {
    fill: var(--background-clr-hero);
  }
</style>
