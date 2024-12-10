<script>
  import Header from "../../components/Header.svelte";
  import ProjectCard from "../../components/ProjectCard.svelte";
  import Footer from "../../components/Footer.svelte";
  import { onMount } from "svelte";

  let devProjects = [];
  let designProjects = [];
  onMount(async () => {
    const response = await fetch('/json/projects.json');
    let projects = await response.json();
    console.log(projects)
    devProjects = projects.filter(project => project.type === "development");
    designProjects = projects.filter(project => project.type === "design");
  });
</script>

<Header />
<main>
  <div class="projects">
    <h2>Projects</h2>
    <div class="projects-development">
      <h3>Development - Latest</h3>
      <section>
        <div><i class="icon-laptop3"></i></div>
        {#each devProjects as project} 
          <ProjectCard 
            projectImg="projects/{project.img}"
            projectName={project.name}
            projectDescription={project.description}
            projectLink={project.link}
          />
        {/each}
        <!-- <ProjectCard projectImg="placeholder-thumbnail.jpeg" projectName="Development Project" projectDescription="Cool project I made this project you want to look yes" />
        <ProjectCard projectImg="placeholder-thumbnail.jpeg" projectName="Development Project" projectDescription="Cool project I made this project you want to look yes" /> -->
      </section>
    </div>
    <div class="projects-design">
      <h3>Design - Latest</h3>
      <section>
        <div><i class="icon-sketchbook3"></i></div>
        {#each designProjects as project} 
          <ProjectCard 
            projectImg="projects/{project.img}"
            projectName={project.name}
            projectDescription={project.description}
            projectLink={project.link}
          />
        {/each}
      </section>
    </div>
  </div>
</main>
<Footer />

<style lang="scss">
  @mixin break($custom) {
    @media (min-width: $custom) { @content; }
  }

  .projects {
    color: var(--accent-two);
    &-development, &-design {
      color: var(--light-text);
      padding: 1em 1.2em;
      border-radius: 25px;

      section {
        display: grid;
        gap: 2em;
        @include break(640px) {
          grid-template-columns: 1fr 1fr;
          align-items: center;
        }
        @include break(1024px) {
          grid-template-columns: 1fr 1fr 1fr;
        }

        div {
          margin-top: 2em;
          &:first-child {
            text-align: center;
          }
          i {
            font-size: 10em;
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
</style>