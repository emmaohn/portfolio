<script>
  import Header from "../../components/Header.svelte";
  import Footer from "../../components/Footer.svelte";

  // import { fade } from 'svelte/transition'
  // import { onMount } from "svelte";	
	// const carouselQuotes = [
	// 	'https://picsum.photos/300/200?random=1',
	// 	'https://picsum.photos/300/200?random=2',
	// 	'https://picsum.photos/300/200?random=3'
	// ]

  // let carouselQuotes = [];
  // onMount(async () => {
  //   const response = await fetch('/json/quotes.json');
  //   carouselQuotes = await response.json();
  //   console.log(carouselQuotes)
  // })
  let carouselQuotes = [];
  async function fetchData() {
    const res = await fetch('/json/quotes.json');
    const data = await res.json();

    if (res.ok) {
      return data;
    } else {
      throw new Error(data);
    }
  }
	
	let index = 0
	
	const next = () => index = (index + 1) % carouselQuotes.length
  const back = () => index === 0 ? index = carouselQuotes.length - 1 : index = (index - 1) % carouselQuotes.length;

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

  <!-- <p bind:value="{index}">{carouselQuotes[index].quote}</p> -->
  <!-- {#each carouselQuotes as quote} -->
  <!-- {#each carouselQuotes as quote (index)} -->
    <!-- <img transition:fade {src} alt="" />
    	 -->
    <!-- {carouselQuotes[0]} -->
    <!-- <p>{console.log(carouselQuotes[index])}</p> -->
    <!-- <p>{JSON.stringify(quote)}</p> -->
  <!-- {/each} -->
  {#await fetchData()}
    <p>Waiting to load quotes!</p>
  {:then quotes}
    {carouselQuotes = quotes}
    <p>{carouselQuotes[index].quote}</p>
  {:catch error}
    <p>{error.message}</p>
  {/await}

  <!-- {#each carouselQuotes as quote, index}
    {#if index == currentCarouselIndex} -->
      <!-- <img src={photo} /> -->
      <!-- {quote}
    {/if}
  {/each} -->

  <button on:click={back}>Back!</button>
  <button on:click={next}>Next!</button>

  <p>{index}</p>
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
</style>
