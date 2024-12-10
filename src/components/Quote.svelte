<script>
  export let quote;
  export let quoter;
  export let title;
</script>

<div class="flex quote">
  <p>{quote}</p>
  <p class="quoter">- {quoter} ({title})</p>
</div>

<style lang="scss">
  .quote {
    flex-direction: column;
    justify-content: space-between;
    background-color: var(--accent-one);
    color: var(--light-text);
    border-radius: 20px;
    min-height: 25vh;
    width: 25vh;
    padding: 1.4em 1.6em;

    p {
      line-height: 22px;
    }
    p:first-child {
      font-weight: 600;
      margin-bottom: 1em;
    }
  }
</style>