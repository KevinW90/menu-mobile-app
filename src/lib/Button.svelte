<script lang="ts">
  export let role: string;
</script>

<div class="button {role}">
  L
</div>

<style lang="scss">
  .button {
    // force to sit on top of all content
    position: relative;
    z-index: 99;
    width: 3rem;
    height: 3rem;
    border-radius: 50%;

    display: flex;
    justify-content: center;
    align-items: center;

    font-size: 1.5rem;
    color: #ddd;

    &.black {
      position: relative;
      z-index: 0;
      background-color: #24282b;
      border: 1px solid rgba(black, .3);

      &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        z-index: -1;
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background: linear-gradient(135deg, rgba(white, .1), rgba(black, .5));
        box-shadow: -2px -2px 15px rgba(255,255,255,.2),
                    2px  2px 15px rgba(0,0,0,.8);
      }
    }
  }
</style>