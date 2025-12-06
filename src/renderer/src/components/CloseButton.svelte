<script>
  import Button from './Button.svelte'
</script>

<Button className="close-button" label="X" onClick={() => window.api.close()} />

<style>
  :global(.close-button) {
    font-size: 14px;
  }
</style>
