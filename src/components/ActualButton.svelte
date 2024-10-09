<script>
  export let bgColor = '--light-background';
  export let textColor = '--dark-text';
  export let handleClick = () => {};
  export let content = '';
  export let isSubmit = false;

  let buttonType = "button";
  if (isSubmit) {
    buttonType = "submit"
  }
</script>

<button type={buttonType} on:click={handleClick}>
  <p style="background-color: var({bgColor}); color: var({textColor});">
    {content} <i class="icon-star1"></i>
  </p>
</button>

<style lang="scss">
  button {
    display: block;
    width: 100%;
    text-align: center;
    margin: .6em 0;
    text-transform: uppercase;
    p:first-child {
      display: inline-block;
      padding: .6em .8em;
      border-radius: 10px;
      font-weight: 600;
      i {
        margin-left: .4em;
      }
    }
  }
</style>