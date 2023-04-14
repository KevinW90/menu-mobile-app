<script lang="ts">
  export let color: string;
  export let size: string;
  export let text: string;
</script>

<div class="button {color} {size}">
  {text}
</div>

<style lang="scss">
  .button {
    // force to sit on top of all content
    position: relative;
    z-index: 99;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: -2px -2px 15px rgba(255,255,255,.2),
                    2px  2px 15px rgba(0,0,0,.8);
    
    &.large {
      width: 3rem;
      height: 3rem;
      font-size: 1.5rem;
    }

    &.small {
      width: 2.5rem;
      height: 2.5rem;
      font-size: 1.25rem;
    }

    &.main {
      width: 100%;
      border-radius: 5rem 0 0 5rem;
      padding: 1rem;
      font-weight: 600;
      &.orange {
        border: none;
        &::before {
          background: none;
        }
      }
    }
    
    &.black {
      position: relative;
      z-index: 0;
      background-color: #24282b;
      border: 1px solid rgba(black, .3);
      color: #ddd;

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
      }
    }

    &.orange {
      position: relative;
      z-index: 0;
      border: 1px solid rgba(black, .8);
      background: linear-gradient(to bottom right, #e17e09, #d24411);
      color: white;

      &::before {
        content: '';
        position: absolute;
        top: 1.5px;
        left: 1.5px;
        z-index: -1;
        width: calc(100% - 3px);
        height: calc(100% - 3px);
        border-radius: 50%;
        background: linear-gradient(135deg, #e63112, #f59006);
      }
      
      &::after {
        content: '';
        position: absolute;
        top: -6px;
        left: -6px;
        z-index: -2;
        width: calc(100% + 12px);
        height: calc(100% + 12px);
        border-radius: 50%;
      }
    }
  }
</style>