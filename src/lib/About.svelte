<script>
  export let goToPage;
</script>

<div>
  <h2>
    I’m a front-end developer who enjoys clean code, good design, and bringing
    ideas to life.
  </h2>
  <p>
    I like building websites that are simple, polished, and effective.<button
      class="underline-animation"
      onclick={() => goToPage("contact")}>Happy to chat</button
    > if you’re interested in working together!
  </p>

  <h1>Welcome</h1>
</div>

<style>
  div {
    margin-left: auto;
  }

  h1 {
    position: fixed;
    bottom: 100px;
    left: 0;
    font-size: 24vw;
    line-height: 0.7;
    color: var(--clr-primary);
    opacity: 0.2;
    z-index: -1;
  }

  h2 {
    text-align: left;
    font-size: 1.9rem;
    margin-bottom: 1rem;
    max-width: 900px;
    margin-left: auto;
  }

  p {
    text-align: left;
  }

  button {
    color: var(--clr-primary);
    transition: 0.2s;
    position: relative;
    font-size: 1rem;
  }

  button:hover {
    color: var(--clr-main);
  }

  @media screen and (min-width: 768px) {
    h1 {
      bottom: 0px;
    }

    h2 {
      text-align: right;
      font-size: 1.9rem;
      margin-bottom: 1rem;
    }

    p {
      text-align: right;
    }
  }
</style>
