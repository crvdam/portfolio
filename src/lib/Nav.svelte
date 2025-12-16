<script>
  import Socials from "./Socials.svelte";

  let { goToPage, activePage } = $props();

  function toggleNav(e) {
    const overlay = document.getElementById("menu-overlay");
    const navList = document.getElementById("nav-items-wrapper");
    const navToggleIcon = document.getElementById("nav-toggle-icon");

    const rect = e.target.getBoundingClientRect();
    const x = rect.left + rect.width / 2;
    const y = rect.top + rect.height / 2;

    overlay.style.left = `${x - window.innerWidth / 2}px`;
    overlay.style.top = `${y - window.innerHeight / 2}px`;

    if (navToggleIcon.classList.contains("open")) {
      navToggleIcon.classList.add("closing");

      setTimeout(() => {
        navToggleIcon.classList.remove("closing");
      }, 300);
    }

    navToggleIcon.classList.toggle("open");
    overlay.classList.toggle("open");
    navList.classList.toggle("open");
  }

  function handleNavClick(page) {
    const navToggleIcon = document.getElementById("nav-toggle-icon");
    const overlay = document.getElementById("menu-overlay");
    const navList = document.getElementById("nav-items-wrapper");

    if (navToggleIcon.classList.contains("open")) {
      navToggleIcon.classList.add("closing");

      setTimeout(() => {
        navToggleIcon.classList.remove("closing");
      }, 300);
    }

    navToggleIcon.classList.remove("open");
    overlay.classList.remove("open");
    navList.classList.remove("open");

    goToPage(page);
  }
</script>

<nav>
  <button
    onclick={toggleNav}
    class="nav-toggle"
    aria-label="Toggle navigation"
    aria-expanded="false"
  >
    <span class="nav-toggle-icon" id="nav-toggle-icon"></span>
  </button>

  <div id="menu-overlay" class="menu-overlay"></div>

  <div class="nav-items-wrapper" id="nav-items-wrapper">
    <ul class="nav-items" id="nav-items">
      <li>
        <button
          class="{activePage === 'about' ? 'active' : ''} underline-animation"
          onclick={() => handleNavClick("about")}>About</button
        >
      </li>
      <!-- <li>
        <button
          class={activePage === "portfolio" ? "active" : ""}
          onclick={() => handleNavClick("portfolio")}>Portfolio</button
        >
      </li> -->
      <li>
        <button
          class="{activePage === 'projects'
            ? 'active'
            : ''} underline-animation"
          onclick={() => handleNavClick("projects")}>Personal projects</button
        >
      </li>
      <li>
        <button
          class="{activePage === 'contact' ? 'active' : ''} underline-animation"
          onclick={() => handleNavClick("contact")}>Contact</button
        >
      </li>
    </ul>

    <div class="socials-wrapper">
      <Socials dark={true} />
    </div>
  </div>
</nav>

<div class="nav-items-wrapper open" style="display: none;"></div>
<span class="menu-overlay open" style="display: none;"></span>
<div class="nav-toggle-icon open closing" style="display: none;"></div>

<style>
  nav {
    opacity: 0;
    animation: fadeIn 1s ease-in forwards;
    animation-delay: 1s;
  }

  .nav-items-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: none;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: flex;
    visibility: hidden;
    z-index: 11;
    opacity: 0;
    transition-delay: 0.2s;
    padding-top: 10rem;
  }

  .nav-items {
    text-align: center;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    color: var(--clr-mobile-menu);
  }

  .socials-wrapper {
    margin-top: auto;
    margin-bottom: 2rem;
  }

  .nav-items button {
    font-size: 1.5rem;
  }

  .nav-items button.active {
    font-weight: 700;
  }

  .menu-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vmax;
    height: 100vmax;
    border-radius: 50%;
    background-color: var(--bg-mobile-menu);
    transform: scale(0);
    transform-origin: center;
    pointer-events: none;
    transition: transform 0.4s ease-in;
    z-index: 10;
  }

  .menu-overlay.open {
    transform: scale(4);
  }

  .nav-items-wrapper.open {
    visibility: visible;
    opacity: 1;
    transition: opacity 0.4s;
    transition-delay: 0.2s;
  }

  .nav-toggle {
    position: relative;
    cursor: pointer;
    z-index: 12;
  }

  .nav-toggle::before {
    content: "";
    position: absolute;
    left: -12px;
    right: -12px;
    bottom: -12px;
    top: -12px;
    background: transparent;
    pointer-events: auto;
  }

  .nav-toggle-icon {
    position: relative;
    display: block;
    z-index: 12;
    transition-delay: 0.2s;
  }

  .nav-toggle-icon,
  .nav-toggle-icon::before,
  .nav-toggle-icon::after {
    height: 3px;
    width: 24px;
    background-color: var(--clr-primary);
  }

  .nav-toggle-icon::before,
  .nav-toggle-icon::after {
    content: "";
    position: absolute;
    left: 0;
  }

  .nav-toggle-icon::before {
    top: -8px;
  }

  .nav-toggle-icon::after {
    bottom: -8px;
  }

  .nav-toggle-icon.open {
    background-color: rgba(0, 0, 0, 0);
    transition-delay: 0.2s;
  }

  .nav-toggle-icon.open::before {
    animation: hamburger-top-open 0.3s ease forwards;
  }

  .nav-toggle-icon.open::after {
    animation: hamburger-bottom-open 0.3s ease forwards;
  }

  .nav-toggle-icon.closing::before {
    animation: hamburger-top-close 0.3s ease forwards;
  }

  .nav-toggle-icon.closing::after {
    animation: hamburger-bottom-close 0.3s ease forwards;
  }

  @keyframes hamburger-top-open {
    40% {
      transform: translateY(8px) rotate(0);
    }
    100% {
      transform: translateY(8px) rotate(45deg);
    }
  }

  @keyframes hamburger-bottom-open {
    40% {
      transform: translateY(-8px) rotate(0);
    }
    100% {
      transform: translateY(-8px) rotate(-45deg);
    }
  }

  @keyframes hamburger-top-close {
    0% {
      transform: translateY(8px) rotate(45deg);
    }
    40% {
      transform: translateY(8px) rotate(0);
    }
    100% {
      transform: translateY(0) rotate(0);
    }
  }

  @keyframes hamburger-bottom-close {
    0% {
      transform: translateY(-8px) rotate(-45deg);
    }
    40% {
      transform: translateY(-8px) rotate(0);
    }
    100% {
      transform: translateY(0) rotate(0);
    }
  }

  @media screen and (min-width: 768px) {
    .nav-toggle {
      display: none;
    }

    .nav-items-wrapper {
      position: static;
      width: unset;
      height: unset;
      visibility: visible;
      opacity: 1;
      padding-top: unset;
    }

    .nav-items {
      flex-direction: row;
      color: var(--clr-desktop-menu);
    }

    .nav-items li {
      padding-left: 5rem;
    }

    .socials-wrapper {
      display: none;
    }

    .nav-items button {
      position: relative;
      background: none;
      border: none;
      color: inherit;
      font: inherit;
      cursor: pointer;
      padding: 0 8px 0 0;
      transition: color 0.3s ease;
    }

    .nav-items button.active {
      font-weight: 400;
    }

    .nav-items button.active::after {
      width: 100%;
    }
  }
</style>
