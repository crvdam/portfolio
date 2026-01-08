<script>
  const currentYear = new Date().getFullYear();
</script>

<footer>
  <!-- <div class="socials">
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
  </div> -->
  <span class="copyright">© <span>{currentYear}</span> - Caspar van Dam</span>
</footer>

<style>
  footer {
    opacity: 0;
    text-align: center;
    transform: translateY(10px);
    animation: fadeIn 1.5s forwards;
    animation-delay: 3s;
    background-color: var(--bg-main);
    padding: 0.5rem 0;
    max-width: 1200px;
    margin: auto;
    margin-top: 0;
    border-top: 1px solid var(--bg-site);
  }

  .copyright {
    color: var(--text-clr-tertiary);
    font-size: 0.8rem;
  }

  @media screen and (min-width: 768px) {
  }
</style>
