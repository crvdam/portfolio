<script>
  let { goToPage, activePage } = $props();
</script>

<nav>
  <ul>
    <li>
      <button
        class={activePage === "about" ? "active" : ""}
        onclick={() => goToPage("about")}>About me</button
      >
    </li>
    <li>
      <button
        class={activePage === "projects" ? "active" : ""}
        onclick={() => goToPage("projects")}>Personal projects</button
      >
    </li>
    <li>
      <button
        class={activePage === "contact" ? "active" : ""}
        onclick={() => goToPage("contact")}>Contact</button
      >
    </li>
  </ul>
</nav>

<style>
  nav {
    font-size: 1rem;
    font-weight: 600;
    opacity: 0;
    animation: fade-in 2s forwards;
    animation-delay: 2s;
    margin: 2rem 0 2rem;
  }

  ul {
    display: flex;
    flex-direction: column;
  }

  li {
    display: inline-block;
  }

  li:not(:last-child) {
    margin-right: 2rem;
  }

  button {
    transition: all 0.3s;
    padding: 0.6rem;
  }

  button:hover,
  .active {
    color: var(--text-clr-primary);
    transform: scale(1.05);
  }

  button:active {
    transform: scale(1);
    transition: all 0s;
  }

  @media screen and (min-width: 768px) {
    nav {
      font-size: 1.3rem;
      margin: 0;
    }

    ul {
      justify-content: left;
    }

    li {
      display: block;
      white-space: nowrap;
    }

    li:not(:last-child) {
      margin-bottom: 2rem;
    }
  }
</style>
