<script>
  export let checked = false
  export let label = ''
  export let disabled = false
  export let onChange = null
</script>

<div>
  <label>
    <input type="checkbox" bind:checked on:change={onChange} {disabled} />
    <span class:disabled>{label}</span>
  </label>
</div>

<style>
  input[type='checkbox'] {
    vertical-align: middle;
    appearance: none;

    width: 13px;
    height: 13px;

    background-image: url('../assets/images/checkbox.png');
    background-repeat: no-repeat;
    background-position: 0 0;

    &:checked {
      background-position: 0 -13px;
    }

    &:disabled {
      background-position: 0 0;
    }
  }
  label span {
    vertical-align: middle;
  }

  .disabled {
    color: #888;
  }
</style>
