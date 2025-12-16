<script>
  export let dark;
</script>

<ul class="socials">
  <li>
    <a
      target="_blank"
      rel="noopener noreferrer"
      href="https://nl.linkedin.com/in/casparvandam"
      class="socials-link {dark ? 'dark' : ''}"
      ><img src="ic-linkedin-dark.png" alt="LinkedIn" /></a
    >
  </li>
  <li>
    <a
      target="_blank"
      rel="noopener noreferrer"
      href="https://https://github.com/crvdam"
      class="socials-link {dark ? 'dark' : ''}"
      ><img src="ic-github-dark.png" alt="GitHub" /></a
    >
  </li>
  <li>
    <a
      href="mailto:casparvandam@gmail.com"
      class="socials-link {dark ? 'dark' : ''}"
      ><img src="ic-email-dark.png" alt="GitHub" /></a
    >
  </li>
  <a style="display:none;" class="socials-link dark"></a>
</ul>

<style>
  ul {
    display: flex;
    gap: 1rem;
  }

  li {
    display: inline-block;
  }

  .socials-link {
    display: inline-block;
    height: 30px;
    width: 30px;
    cursor: pointer;

    img {
      filter: brightness(0) invert(1);

      &:hover {
        transition: filter 0.2s ease;
        filter: unset;
      }
    }

    &.dark {
      img {
        filter: brightness(0) invert(0);

        &:hover {
          transition: filter 0.2s ease;
          filter: unset;
        }
      }
    }
  }
</style>
