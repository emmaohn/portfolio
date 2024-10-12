<hr>
<footer>
  <div class="info-text">
    <div class="info-text_me">
      <span class="bold">Jojo Johnson</span>
      <p>Designer and Developer</p>
    </div>
    <div class="info-text_contact">
      <p><span class="bold">Email:</span><a href="mailto:emmaohn00@gmail.com">emmaohn00@gmail.com</a></p>
      <p><span class="bold">Phone:</span><a href="tel:8176598369">(817) 659-8369</a></p>
    </div>
  </div>
  <div class="socials_mobile flex">
    <a href="https://www.linkedin.com/in/jojo-johnson/"><img src="images/social/linkedin.svg" alt="LinkedIn icon"></a>
    <a href="https://www.behance.net/jojo-johnson/"><img src="images/social/behance.svg" alt="Behance icon"></a>
    <a href="https://github.com/emmaohn/"><img src="images/social/github.svg" alt="GitHub icon"></a>
    <a href="https://www.pinterest.com/emmaohn00/"><img src="images/social/pinterest.svg" alt="Pinterest icon"></a>
  </div>
  <div class="socials_desktop">
    <a target="_blank" href="https://www.linkedin.com/in/jojo-johnson/"><p>https://www.linkedin.com/in/jojo-johnson/</p><img src="images/social/linkedin.svg" alt="LinkedIn icon"></a>
    <a target="_blank" href="https://www.behance.net/jojo-johnson/"><p>https://www.behance.net/jojo-johnson/</p><img src="images/social/behance.svg" alt="Behance icon"></a>
    <a target="_blank" href="https://github.com/emmaohn/"><p>https://github.com/emmaohn/</p><img src="images/social/github.svg" alt="GitHub icon"></a>
    <a target="_blank" href="https://www.pinterest.com/emmaohn00/"><p>https://www.pinterest.com/emmaohn00/</p><img src="images/social/pinterest.svg" alt="Pinterest icon"></a>
  </div>
</footer>

<style lang="scss">
  @mixin break($custom) {
    @media (min-width: $custom) { @content; }
  }

  .bold {
    font-weight: 600;
  }

  hr {
    border: 2px solid var(--dark-text);
    background-color: var(--dark-text);
    border-radius: 100px;
    margin-top: 2em;
  }

  footer {
    padding: 1em 0;
    margin-top: 0;
    margin-bottom: 1.6em;
    text-align: center;

    @include break(1024px) {
      text-align: left;
      display: flex;
      justify-content: space-around;
    }
  }

  .info-text {
    &_contact {
      margin-top: 1em;

      span {
        margin-right: .2em;
      }
    }
  }

  .socials {
    &_mobile {
      justify-content: center;
      margin-top: 1em;
      img {
        margin: 0 .4em;
      }

      @include break(1024px) {
        display: none;
      }
    }
    &_desktop {
      display: none;

      @include break(1024px) {
        display: block;
      }
      a {
        display: flex;
        justify-content: flex-end;
        margin-top: .6em;

        img {
          margin-left: .4em;
        }
      }
    }
  }
</style>