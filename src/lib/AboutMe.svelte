<script></script>

<section class="aboutMe">
  <article class="aboutMe__article">
    <h3 class="aboutMe__tile">About Me</h3>
    <p class="aboutMe__indent">
      I found my passion for coding later in life, sitting at home during the
      COVID lockdowns. While working as a chef, I began teaching myself how to
      program, bit by bit, dedicating time after shifts to learn and build.
      After a couple of years of self-teaching and project work, I made the leap
      into tech and landed my first role as a Junior Frontend Developer.
    </p>

    <p class="aboutMe__indent">
      I still spend much of my free time learning about software development,
      building personal projects, and exploring new technologies. It's become a
      genuine passion, something I never get tired of.
    </p>

    <p class="aboutMe__indent">
      When I'm not coding, there's a good chance you'll find me cooking,
      listening to music, playing the drums, or watching films. If I manage to
      get myself outside, you might even spot me at a bouldering gym, lifting
      weights, or going for a run.
    </p>
  </article>

  <article class="aboutMe__article">
    <h3 class="aboutMe__eduction">Education</h3>
    <ul class="aboutMe__indent">
      <li>
        <p class="aboutMe__degree">Bachelor's Clinical Psychology</p>
        <p>Utrecht University</p>
      </li>
      <li>
        <p class="aboutMe__degree">
          Bachelor's Industrial-organizational Psychology
        </p>
        <p>Utrecht University</p>
      </li>
      <li>
        <p class="aboutMe__degree">
          Master's Industrial-Organizational Psychology
        </p>
        <p>Utrecht University</p>
      </li>
    </ul>
  </article>

  <article class="aboutMe__article">
    <h3 class="aboutMe__experience">Career</h3>
    <ul class="aboutMe__indent aboutMe__careerList">
      <li>
        <p><strong>Chef de partie / Sous-chef / Head-chef</strong></p>
        <p>
          9+ years of experience as a chef, working across a wide range of
          kitchens, from casual to fine dining.
        </p>
        <p>2016 - 2025</p>
      </li>
      <li>
        <p><strong>Junior Frontend Developer</strong> - Accessify</p>
        <p>March 2025</p>
        <p class="aboutMe__jobDescription">
          I develop new templates, improve UI/UX, and resolve bugs for
          Accessify's SaaS platform, used by over 50 clients. I also help ensure
          client websites meet performance, accessibility, and SEO best
          practices.
        </p>
      </li>
    </ul>
  </article>
</section>

<style>
  .aboutMe {
    max-width: 1000px;
    margin: auto;
    padding: 10rem 0;
    color: var(--background-clr-card);

    h3 {
      color: var(--text-clr-primary);
      margin-bottom: 1rem;
    }
  }

  .aboutMe__article {
    margin-bottom: 5rem;
  }

  .aboutMe__indent {
    margin-bottom: 1rem;
    padding-left: 1rem;
    text-align: justify;
  }

  li {
    margin-bottom: 1rem;
  }

  .aboutMe__degree {
    font-weight: 700;
  }

  .aboutMe__careerList {
    list-style-type: disc;
    margin-left: 1rem;

    li {
      padding-left: 1rem;
      margin-bottom: 2rem;
    }

    li::marker {
      color: var(--text-clr-primary);
    }
  }
</style>
