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
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    color: var(--text-clr-tertiary);
    height: 4rem;
    font-size: 0.7rem;
    opacity: 0;
    animation: fade-in 2s forwards;
    animation-delay: 2.5s;
    margin-top: 6rem;
  }

  .copyright {
    margin-top: 1rem;
    margin-left: auto;
    margin-right: auto;
    align-self: flex-end;
  }

  .socials {
    height: 100%;

    a {
      display: inline-block;
    }
  }

  @media screen and (min-width: 768px) {
    footer {
      flex-direction: row;
      margin-top: unset;
    }

    .socials {
      margin-top: 4rem;
    }
  }
</style>
