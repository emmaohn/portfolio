<script>
  import { fade } from "svelte/transition";
  let isOpen = false;
  function openMenu() {
    isOpen = !isOpen;
  }
</script>

<header class="items-center my-4">
  <div class="flex justify-between">
    <a href="/"><img src="/svgs/logo.svg" alt="Jojo Johnson logo"></a>
    <button on:click={openMenu}>
      <img class="mobile-bars md:hidden" src="/svgs/bars.svg" alt="hamburger menu">
    </button>
    <nav class="hidden md:block">
      <ul class="desktop flex">
        <a href="/#skills"><li>Skills</li></a>
        <a href="/projects"><li>Projects</li></a>
        <a href="/about-me"><li>About Me</li></a>
        <a href="/#contact-me"><li>Contact</li></a>
      </ul>
    </nav>
  </div>
  {#if isOpen}
    <nav in:fade={{ duration: 200 }} out:fade={{ duration: 200 }} class="{isOpen ? "block" : "hidden"} md:hidden">
      <ul class="mobile">
        <a on:click={() => {isOpen = false}} href="/#skills"><li>Skills</li></a>
        <a href="/projects"><li>Projects</li></a>
        <a href="/about-me"><li>About Me</li></a>
        <a on:click={() => {isOpen = false}} href="/#contact-me"><li>Contact</li></a>
      </ul>
    </nav>
  {/if}
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
    font-size: 2em;
    position: fixed;
    top: 73px;
    left: 0;
    right: 0;
    height: 100vh;
    /* fix nav height on mobile safari, where 100vh is a little off */
    height: -webkit-fill-available;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    background: var(--light-background);

    a:first-child {
      margin-top: -2em;
    }
    li {
      transition: all .3s;
      padding: .3em;

    }
    li:first-child:hover {
      transform: scale(1.2);
    }
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