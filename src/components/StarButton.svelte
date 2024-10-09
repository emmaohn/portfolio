<script>
  export let bgColor = '--light-background';
  export let textColor = '--dark-text';
  export let textAlignMobile = 'center';
  export let textAlignDesktop = 'center';
  export let href = '';
  export let content = '';
</script>

<a href="{href}" class="text-{textAlignMobile} md:text-{textAlignDesktop}">
  <p style="background-color: var({bgColor}); color: var({textColor});">
    {content} <i class="icon-star1"></i>
  </p>
</a>

<style lang="scss">
  a {
    display: block;
    width: 100%;
    margin: .6em 0;
    text-transform: uppercase;

    p:first-child {
      display: inline-block;
      padding: .4em .6em;
      border-radius: 10px;
      font-weight: 600;
      font-size: .9em;
      i {
        margin-left: .4em;
        font-size: 1.2em;
      }
    }
  }
</style>