<script>
  export let bgColor = '--light-background';
  export let textColor = '--dark-text';
  export let smallAlign = "left";
  export let medAlign = "left";
  export let href = '';
  export let content = '';
</script>

<a href="{href}" class="small-{smallAlign} med-{medAlign}">
  <p style="background-color: var({bgColor}); color: var({textColor});">
    {content} <i class="icon-star1"></i>
  </p>
</a>

<style lang="scss">
  @mixin break($custom) {
    @media (min-width: $custom) { @content; }
  }

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
  .small-left {
    text-align: left;
  }
  .small-center {
    text-align: center;
  }
  .med-left {
    @include break(768px) {
      text-align: left;
    }
  }
  .med-center {
    @include break(768px) {
      text-align: center;
    }
  }
</style>