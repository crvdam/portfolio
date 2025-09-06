<script>
  import Header from "./lib/Header.svelte";
  import Nav from "./lib/Nav.svelte";
  import Main from "./lib/Main.svelte";
  import Footer from "./lib/Footer.svelte";

  let activePage = $state("");

  const text =
    "Chef turned developer. I bring the same care and attention to detail from the kitchen to code, aiming to create clean, user-friendly interfaces. Life-long learner, passionate about coding and always curious. I am open to freelance opportunities";
  const textArray = text.split(" ");

  function goToPage(page) {
    activePage = page;
  }

  function preloadImages(sources) {
    sources.forEach((src) => {
      const img = new Image();
      img.src = src;
    });
  }

  preloadImages([
    "/project-placeholer.webp",
    "/project-messenger.webp",
    "/project-realestate.webp",
    "/project-movies.webp",
    "/project-portrait.webp",
  ]);

  import { onMount } from "svelte";

  if (window.innerWidth > 1000) {
    const scriptThree = document.createElement("script");
    scriptThree.src =
      "https://cdnjs.cloudflare.com/ajax/libs/three.js/r121/three.min.js";
    document.body.appendChild(scriptThree);

    const scriptVanta = document.createElement("script");
    scriptVanta.src =
      "https://cdn.jsdelivr.net/npm/vanta/dist/vanta.waves.min.js";
    document.body.appendChild(scriptVanta);
  }

  onMount(() => {
    if (window.innerWidth > 1000) {
      VANTA.CELLS({
        el: "#app",
        mouseControls: true,
        touchControls: true,
        gyroControls: false,
        minHeight: 200.0,
        minWidth: 200.0,
        scale: 1,
        color1: 0x422,
        color2: 0x112031,
        size: 4,
        speed: 0.4,
      });
    }
  });
</script>

<div class="container" id="container">
  <Header />
  <div class="nav-main-container">
    <Nav {goToPage} {activePage} />
    <Main {activePage} />
  </div>
  <Footer />
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    color: var(--text-clr-secondary);
    min-height: calc(100vh - 1rem);
    position: relative;
    border: 1px solid var(--text-clr-primary);
    padding: 1rem;
  }

  .nav-main-container {
    display: flex;
    flex-direction: column;
    flex: 1;
    height: calc(100% - 150px);
  }

  @media screen and (min-width: 768px) {
    .container {
      min-height: calc(100vh - 4rem);
    }
    .nav-main-container {
      flex-direction: row;
      align-items: center;
    }
  }
</style>
