<script>
  export let imgSrc = '';
  export let starAmount = 0;
</script>

<div class="flex items-center my-4">
  <img src="{imgSrc}" alt="{imgSrc}">
  {#each {length: starAmount - 1} as star}
    <i class="icon-star3"></i>
  {/each}
  <i class="icon-star3"></i>
</div>

<style>
  img {
    width: 50px;
    margin-right: 1em;
  }
  i {
    font-size: 1.4em;
    margin-left: .7em;
    color: var(--accent-one);
  }
</style>