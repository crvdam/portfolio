<script>
  export let goToPage;
</script>

<div>
  <h1>
    Chef turned front-end developer. 
  </h1>
  <h2>Lifelong learner with a love for code.</h2>
  <p>
    I like building websites that are simple, polished, and effective. <button
      class="underline-animation"
      onclick={() => goToPage("contact")}>Happy to chat</button
    > if you’re interested in working together!
  </p>
</div>

<style>
  div {
    margin-top: 2rem;
    margin-left: auto;
  }

  h1 {
    margin-bottom: 1rem;
  }

  h2 {
    margin-bottom: 2rem;
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

  }
</style>
