<script lang="ts">
  import { onMount } from "svelte";

  let mainEl: HTMLElement;
  let centerEl: HTMLElement;
  onMount(() => {
    mainEl = document.querySelector("main");
    centerEl = document.querySelector(".center");

    // get dimensions of main element
    const mainWidth = mainEl.offsetWidth;
    
    // 2rem margin from edge of screen
    const margin = 2;
    // 
    centerEl.style.width = `${mainWidth - (2 * (margin * 16))}px`;
    centerEl.style.height = `${mainWidth - (2 * (margin * 16))}px`;
});
</script>

<main>
  <div class="center">

  </div>
</main>

<style lang="scss">
  $dark: hsl(220, 5%, 13%);
  $bg-start: hsl(213, 10%, 23%);
  $bg-end: hsl(228, 9%, 11%);
  
  main {
    width: 100vw;
    height: 100vh;

    background: linear-gradient(180deg, $bg-start, $bg-end);
  }

  // sunken area behind focus circle
  .center {
    // used to place ::before, ::after according to this element
    position: relative;
    border-radius: 50%;
    margin: 0 auto;
    background: linear-gradient(135deg, rgba($dark, .6), rgba(#aaa, .1));
    box-shadow: -5px -5px 5px 0 rgba(black, .1), 5px 5px 5px rgba(#505050,.3);
    transform: translateY(50%);

    // dark circle as the focus element
    // will conatin the image
    &::before {
      content: '';
      position: absolute;
      // shift element to center
      top: 1rem;
      left: 1rem;
      z-index: 0;
      // subtract 1rem from each side
      width: calc(100% - 2rem);
      height: calc(100% - 2rem);
      border-radius: 50%;
      background-color: $dark;
    }

    // forms the bottom-most rounded edge
    // where the S,M,L buttons will be
    &::after {
      content: '';
      position: absolute;
      // shift element to center
      top: calc(-50% - 2rem);
      left: calc(-50% - 2rem);
      z-index: -1;
      transform: translateY(-10%);
      // must match height for circular shape
      width: calc(200% + 4rem);
      // must be tall enough to cover top of screen
      height: calc(200% + 4rem);
      border-radius: 50%;
      // layering issues means this is between sunken area and focus circle
      // transparent bg allows the sunken area to show through, plus this doesn't need to be visible
      background-color: transparent;
      // sharp black shadow at base
      box-shadow: inset 0 0 2rem 0 rgba(black, .3);
    }
  }
</style>
