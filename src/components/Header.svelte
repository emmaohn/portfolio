<!-- <script>
  export let imgSrc = '';
  export let starAmount = 0;
</script> -->

<header class="items-center my-4">
  <div class="flex justify-between">
    <img src="/svgs/logo.svg" alt="">
    <button>
      <img class="mobile-bars md:hidden" src="/svgs/bars.svg" alt="">
    </button>
    <nav class="hidden">
      <ul class="mobile">
        <li>Skills</li>
        <li>Projects</li>
        <li>About Me</li>
        <li>Contact</li>
      </ul>
    </nav>
    <nav class="hidden md:block">
      <ul class="desktop flex">
        <a href="#skills"><li>Skills</li></a>
        <a href="#projects"><li>Projects</li></a>
        <a href="#about-me"><li>About Me</li></a>
        <a href="#contact-me"><li>Contact</li></a>
      </ul>
    </nav>
  </div>
  <hr>
</header>

<style lang="scss">
  header {
    background-color: var(--light-background);
    background: rgb(2,0,36);
    background: linear-gradient(0deg, rgba(2,0,36,0) 0%, var(--light-background) 25%);
    position: sticky;
    top: 0px;
    z-index: 100;
    padding: 1em 0;
    margin-top: 0;
  }
  hr {
    border: 2px solid var(--dark-text);
    background-color: var(--dark-text);
    border-radius: 100px;
  }
  img {
    width: 50px;
    margin: 0 .6em;
    padding-bottom: 1em;
  }
  .mobile {
    text-transform: uppercase;
    &-bars {
      width: 30px;
    }
  }
  .desktop {
    li {
      padding: .2em .6em;
      margin: 0 .2em;
      &:active, &:focus-visible {
        background-color: var(--dark-background);
        color: var(--light-text);
        border-radius: 15px;
      }
    }
  }
</style>