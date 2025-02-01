<script>
  import Header from "../components/Header.svelte";
  import StarButton from "../components/StarButton.svelte";
  import ProjectCard from "../components/ProjectCard.svelte";
  import Footer from "../components/Footer.svelte";
  import { onMount } from "svelte";

  let devSkills = [];
  let designSkills = [];

  let latestDevelopmentProject = {};
  let latestDesignProject = {};
  onMount(async () => {
    const skillResponse = await fetch('/json/skills.json');
    let skills = await skillResponse.json();
    // console.log(skills)
    devSkills = skills.filter(skill => skill.type === "development");
    designSkills = skills.filter(skill => skill.type === "design");

    const projectResponse = await fetch('/json/projects.json');
    let projects = await projectResponse.json();
    latestDevelopmentProject = projects.filter(project => project.type === "development").at(-1);
    latestDesignProject = projects.filter(project => project.type === "design").at(-1);
    // console.log(latestDevelopmentProject)
  });

  let formName = "";
  let formEmail = "";
  let formPhone = "";
  let formMessage = "";
</script>

<Header />
<main>
  <!-- Mobile intro!! -->
  <div class="intro">
    <div class="title md:hidden">
      <div class="flex">
        <h1>Jojo Johnson</h1>
        <i class="icon-star3"></i>
      </div>
      <h3>Designer &amp; Developer</h3>
    </div>
    <div class="pic-of-me relative">
      <i class="icon-heart3 heart absolute"></i>
      <img src="/images/me.JPG" alt="Jojo Johnson">
    </div>
    <div>
      <div class="title hidden md:block">
        <div class="flex">
          <h1>Jojo Johnson</h1>
          <i class="icon-star3"></i>
        </div>
        <h3>Designer &amp; Developer</h3>
      </div>
      <div>
        <p>"A passionate developer who brings style into development."</p>
        <p>- Levi Jones (Software Dev)</p>
      </div>
      <StarButton 
        bgColor="--accent-one" 
        textColor="--light-text"
        medAlign="left"
        href="" 
        content="See more"
      />
    </div>
    <!-- link to about me section -->
  </div>
  <!-- Desktop intro!! -->

  <!-- Skills and stars!! -->
  <a id="skills">
    <div class="skills">
      <h2>Skills/Tools</h2>
      <div class="skills-icons">
        <div>
          <h4>Development</h4>
          <div class="flex flex-wrap">
            {#each devSkills as skill}
              <div class="skills-skill">
                <img src="/images/skills/{skill.imgName}" alt="{skill.imgName}">
                <!-- <p>{skill.skill}</p> -->
              </div>
            {/each}
          </div>
        </div>
        <div>
          <h4>Design</h4>
          <div class="flex flex-wrap">
            {#each designSkills as skill}
            <div class="skills-skill">
              <img src="/images/skills/{skill.imgName}" alt="{skill.imgName}">
              <!-- <p>{skill.skill}</p> -->
            </div>
            {/each}
          </div>
        </div>
      </div>
    </div>
  </a>

  <!-- Projects!! -->
  <a id="projects">
    <div class="projects">
      <h2>Projects</h2>
      <div class="projects-development">
        <h3>Development - Latest</h3>
        <section>
          <div><i class="icon-laptop3"></i></div>
          <div>
            <ProjectCard 
              projectImg="{latestDevelopmentProject.img}"
              projectName="{latestDevelopmentProject.name}"
              projectDescription="{latestDevelopmentProject.description}" 
              projectLink="{latestDevelopmentProject.link}" 
            />
            <!-- link to projects -->
            <StarButton 
              bgColor="--light-background" 
              textColor="--accent-two" 
              smallAlign="center"
              content="See More" 
              href="/projects" 
            />
          </div>
        </section>
      </div>
      <div class="projects-design">
        <h3>Design - Latest</h3>
        <section>
          <div><i class="icon-sketchbook3"></i></div>
          <div>
            <ProjectCard 
              projectImg={latestDesignProject.img} 
              projectName={latestDesignProject.name} 
              projectDescription={latestDesignProject.description} 
              projectLink={latestDesignProject.link} 
            />
            <!-- link to projects -->
            <StarButton 
              bgColor="--light-background" 
              textColor="--accent-one"
              smallAlign="center" 
              content="See More" 
              href="/projects" 
            />
          </div>
        </section>
      </div>
    </div>
  </a>

  <!-- About Me!! -->
  <a id="about-me">
    <div class="about-me">
      <h2>About Me</h2>
      <div class="about-me_mobile">
        <div class="about-me_icon"><i class="icon-me"></i></div>
        <p>Hi, I'm Jojo Johnson! I am a web designer and developer from Fort Worth, Texas. I studied and fell in love with web at BYU-Idaho.</p>
        <p>I had never programmed before college, and, in fact, I was a math education major when I first began attending BYU-I! Now I am proud to say I was the director of the computing drop-in lab and helped tens of students with python, c#, and, of course, anything web related.</p>
        <p>Apart from coding and designing, I enjoy spending time with loved ones, rock climbing, curating my closet, and scouting out the best food spots!</p>
        <p>I am enthusiastic about my work, and I hope that it reflects my dedication and passion for the craft!</p>
        <!-- link to about me page -->
        <StarButton 
          bgColor="--accent-one" 
          textColor="--light-text" 
          content="More About Me" 
          href="/about-me" 
        />
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
          <!-- link to about me page -->
          <StarButton 
            bgColor="--accent-one" 
            textColor="--light-text" 
            smallAlign="center"
            medAlign="center"
            content="More About Me" 
            href="/about-me" 
          />
        </div>
      </div>
    </div>
  </a>

  <!-- Contact Me!! -->
  <a id="contact-me">
    <div class="contact-me">
      <h2>Let's Get in Contact</h2>
      <form action="mailto:emmaohn01@gmail.com?
        subject=Message+to+Jojo+Johnson
        &body=Name:{formName}+Email:{formEmail}+Phone:{formPhone}+Message:{formMessage}" >
        <p>I am currently looking for work! If any of my work interests you, please reach out and let me know!</p>

        <div>
          <label for="name"><span>Name</span> (optional)</label>
          <input name="name" id="name" type="text" bind:value={formName}>
    
          <label for="email"><span>Email</span> (optional)</label>
          <input name="email" id="email" type="email" bind:value={formEmail}>
    
          <label for="phone"><span>Phone</span> (optional)</label>
          <input name="phone" id="phone" type="text" bind:value={formPhone}>
    
          <label for="message"><span>Message</span></label>
          <textarea name="message" id="message" bind:value={formMessage} required></textarea>
    
          <StarButton 
            bgColor="--light-background" 
            textColor="--accent-two" 
            smallAlign="centers"
            content="Send"
            href="mailto:emmaohn01@gmail.com?
                  &subject=Message%20to%20Jojo%20Johnson
                  &body=Name:%20{formName}%0AEmail:%20{formEmail}%0APhone:%20{formPhone}%0AMessage:%20{formMessage}" 
          />
        </div>
      </form>
    </div>
  </a>
</main>
<Footer />

<style lang="scss">
  @mixin break($custom) {
    @media (min-width: $custom) { @content; }
  }

  .skills h2, .projects h2, .about-me h2, .contact-me h2 {
    margin-top: 2em;
    
    @include break(768px) {
      margin-top: 1.4em;
    }
  }

  .skills > :last-child, .projects > :last-child, .about-me > :last-child {
    margin-bottom: -2em;
    
    @include break(768px) {
      margin-bottom: 0;
    }
  }

  .intro {
    .title {
      h1, i {
        color: var(--accent-one);
      }
      h1 {
        text-wrap: nowrap;
      }
      h3 {
        color: var(--accent-two);
      }
      i {
        margin-left: 5px;
        margin-top: 10px;
        font-size: 45px;
      }
    }
    .pic-of-me  {
      margin: 1.6em;
      max-width: 325px;
      margin: 1.4em auto;
      transition: all .45s;

      @include break(768px) {
        max-width: 270px;
      }
      @include break(1024px) {
        max-width: 350px;
      }
  
      .heart {
        font-size: 3em;
        color: var(--accent-two);
        top: -15px;
        left: -15px;
        transform: rotateZ(-30deg);
      }
      img {
        border: 6px solid var(--accent-two);
        border-radius: 25px;
      }
    }
    @include break(768px) {
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
    }
  }
  .skills {
    h2 {
      color: var(--accent-one);
    }
    &-skill {
      color: var(--accent-one);
      font-weight: bolder;
      text-align: center;
      margin-right: .8em;
      margin-top: 1em;
      @include break(768px) {
        margin-right: 1em;
        margin-top: 1.2em;
      }
    }
    &-icons {
      border: 6px solid var(--accent-one);
      border-radius: 25px;
      padding: 0 1em 1em 1em;
      @include break(640px) {
        display: grid;
        grid-template-columns: 1fr 1fr;
      }

      > div:first-child {
        @include break(640px) {
          margin-right: 1em;
        }
      }
      > div:nth-child(2) {
        @include break(640px) {
          margin-left: 1em;
        }
      }
      img {
        width: 50px;
        @include break(768px) {
          width: 60px;
        }
      }
      h4 {
        margin-top: 1em;
        margin-bottom: -.2em;
        color: var(--accent-one);
      }
    }
  }
  .projects {
    color: var(--accent-two);
    &-development, &-design {
      color: var(--light-text);
      padding: 1em 1.2em;
      border-radius: 25px;

      section {
        @include break(640px) {
          display: grid;
          grid-template-columns: 6fr 5fr;
          align-items: center;
        }

        div {
          margin-top: 2em;
          &:first-child {
            text-align: center;
          }
          i {
            font-size: 10em;
            @include break(1024px) {
              font-size: 15em;
            }
          }
        }
      }
    }
    &-development {
      background-color: var(--accent-two);
      margin-bottom: 1em;
    }
    &-design {
      background-color: var(--accent-one); 
    }
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
  .contact-me {
    color: var(--accent-two);
    form {
      background-color: var(--accent-two);
      color: var(--light-text);
      border-radius: 25px;
      padding: 1.2em;
      @include break(768px) {
        display: grid;
        grid-template-columns: 1fr 1fr;
        padding: 2em 3em;
      }
      @include break(1024px) {
        padding: 3em 5em;
      }

      p {
        margin-bottom: 1.6em;
        @include break(768px) {
          padding-right: 5em;
        }
        @include break(1024px) {
          padding-right: 10em;
        }
      }
      label {
        font-size: 24px;
        > span {
          font-weight: 800;
        }
      }
      input, textarea {
        display: block;
        background-color: var(--light-background);
        color: var(--accent-two);
        font-size: 1.2em;
        width: 100%;
        height: 45px;
        border-radius: 15px;
        margin-bottom: .8em;
        margin-top: .4em;
        padding: 1em;
      }
      textarea {
        height: 150px;
        margin-bottom: 1.4em;
      }
    }
  }
</style>