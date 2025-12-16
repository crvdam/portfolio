<script>
  import Header from "./lib/Header.svelte";
  import Main from "./lib/Main.svelte";
  import Footer from "./lib/Footer.svelte";

  let activePage = $state("about");

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
</script>

<div class="site">
  <Header {activePage} {goToPage} />
  <Main {activePage} {goToPage} />
  <!-- <Footer /> -->
</div>

<style>
  @media screen and (min-width: 768px) {
  }
</style>
