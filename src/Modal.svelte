<script>
  import { fade } from 'svelte/transition';
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
</script>

<div class="modal-background" transition:fade="{{delay: 0, duration: 300}}"></div>

<div class="modal" on:click="{() => dispatch('close')}" transition:fade="{{delay: 0, duration: 300}}">
  <div class="modal-header">
    <button class="close" on:click="{() => dispatch('close')}">&times;</button>
    <slot name="header"></slot>
  </div>

  <slot></slot>

  <div class="modal-footer">
    <button on:click="{() => dispatch('close')}">Close</button>
  </div>
</div>

<style>
  .modal-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.3);
    z-index: 99;
  }

  .modal {
    position: absolute;
    left: 50%;
    top: 50%;
    width: calc(100vw - 4em);
    max-width: 32em;
    max-height: calc(100vh - 4em);
    overflow: auto;
    transform: translate(-50%,-50%);
    padding: 1em;
    border-radius: 0.2em;
    background: white;
    z-index: 999;
  }

  .close {
    float: right;
  }
</style>