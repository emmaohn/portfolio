<script>
  import Header from "../../components/Header.svelte";
  import Quote from "../../components/Quote.svelte";
  import Footer from "../../components/Footer.svelte";
  import { onMount } from "svelte";

  let carouselQuotes = [];
  onMount(async () => {
    const response = await fetch('/json/quotes.json');
    let quotes = await response.json();
    console.log(quotes)
    carouselQuotes = quotes;
  });
	
	let currIndex = 0
	
	const next = () => currIndex = (currIndex + 1) % carouselQuotes.length
  const back = () => currIndex === 0 ? currIndex = carouselQuotes.length - 1 : currIndex = (currIndex - 1) % carouselQuotes.length;

</script>

<Header />
<main>
  <div class="about-me">
    <h2>About Me</h2>
    <div class="about-me_mobile">
      <div class="about-me_icon"><i class="icon-me"></i></div>
      <p>Hi, I'm Jojo Johnson! I am a web designer and developer from Fort Worth, Texas. I studied and fell in love with web at BYU-Idaho.</p>
      <p>I had never programmed before college, and, in fact, I was a math education major when I first began attending BYU-I! Now I am proud to say I was the director of the computing drop-in lab and helped tens of students with python, c#, and, of course, anything web related.</p>
      <p>Apart from coding and designing, I enjoy spending time with loved ones, rock climbing, curating my closet, and scouting out the best food spots!</p>
      <p>I am enthusiastic about my work, and I hope that it reflects my dedication and passion for the craft!</p>
    </div>
    <div class="about-me_desktop">
      <div>
        <p>Hi, I'm Jojo Johnson! I am a web designer and developer from Fort Worth, Texas. I studied and fell in love with web at BYU-Idaho.</p>
        <p>I had never programmed before college, and, in fact, I was a math education major when I first began attending BYU-I! Now I am proud to say I was the director of the computing drop-in lab and helped tens of students with python, c#, and, of course, anything web related.</p>
        <p>Apart from coding and designing, I enjoy spending time with loved ones, rock climbing, curating my closet, and scouting out the best food spots!</p>
        <p>I am enthusiastic about my work, and I hope that it reflects my dedication and passion for the craft!</p>
      </div>
      <div>
        <div class="about-me_icon"><i class="icon-me"></i></div>
      </div>
    </div>
  </div>

  
  <div class="flex justify-between">
    <button class="navigation-buttons" on:click={back}><p>&lt</p></button>
    {#if carouselQuotes.length}
      {#each carouselQuotes as quote, index}
        {#if index == currIndex}
          <!-- {quote.quote} -->
          <Quote 
            quote={quote.quote}
            quoter={quote.quoter}
            title={quote.title}
          />
        {/if}
      {/each}
    {/if}
    <button class="navigation-buttons" on:click={next}><p>&gt</p></button>
  </div>

</main>
<Footer />

<style lang="scss">
  @mixin break($custom) {
    @media (min-width: $custom) { @content; }
  }

  .about-me {
    color: var(--accent-one);
    &_icon {
      font-size: 280px;
      text-align: center;
      margin: -55px 0;
      transform: scaleX(-1);
    }
    p {
      color: var(--dark-text);
      margin: 0 1.4em 1em 1.4em;
      @include break(768px) {
        margin: 0;
        margin-bottom: 1em;
        margin-right: 1em;
      }
    }
    
    &_mobile {
      @include break(768px) {
        display: none;
      }
    }
  
    &_desktop {
      display: none;
      @include break(768px) {
        display: grid;
        grid-template-columns: 2fr 1fr;
      }
    }
  }

  .navigation-buttons {
    display: inline-block;
    // width: 100%;
    margin: .6em 0;
    p {
      display: inline-block;
      color: var(--accent-two);
      // padding: .4em .8em;
      border-radius: 10px;
      font-weight: 700;
      font-size: 4em;
    }
  }
</style>
