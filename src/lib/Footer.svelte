<script>
  const currentYear = new Date().getFullYear();
</script>

<footer>
  <div class="socials">
    <a
      target="_blank"
      rel="noopener noreferrer"
      href="https://nl.linkedin.com/in/casparvandam"
      class="icon"><img src="ic-linkedin-dark.png" alt="LinkedIn" /></a
    >
    <a
      target="_blank"
      rel="noopener noreferrer"
      href="https://https://github.com/crvdam"
      class="icon"><img src="ic-github-dark.png" alt="GitHub" /></a
    >
    <a href="mailto:casparvandam@gmail.com" class="icon"
      ><img src="ic-email-dark.png" alt="GitHub" /></a
    >
  </div>
  <span class="copyright">© <span>{currentYear}</span> - Caspar van Dam</span>
</footer>

<style>
  footer {
    display: flex;
    align-items: center;
    flex-direction: column;
    width: 100%;
    margin: auto;
    opacity: 0;
    animation: fade-in 2s forwards;
    animation-delay: 2.5s;
  }

  .copyright {
    color: var(--text-clr-tertiary);
    font-size: 0.6rem;
    margin-bottom: 0.5rem;
  }

  .socials {
    height: 100%;
    margin-bottom: 1rem;

    a {
      display: inline-block;
    }
  }

  @media screen and (min-width: 768px) {
  }
</style>
