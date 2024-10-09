<script>
  export let projectImg;
  export let projectName;
  export let projectDescription;
</script>

<div class="project-card">
  <img src="/images/{projectImg}" alt="{projectName}">
  <div class="project-card-description">
    <h5>{projectName}</h5>
    <p>{projectDescription}</p>
  </div>
</div>

<style lang="scss">
  .project-card {
    color: var(--dark-text);
    img {
      border: 6px solid var(--light-background);
      border-radius: 20px 20px 0 0;
    }
    &-description {
      background-color: var(--light-background);
      padding: .4em 1em;
      border-radius: 0 0 20px 20px;
      h5 {
        font-weight: 700;
      }
    }
  }
</style>