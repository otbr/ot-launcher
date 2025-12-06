<script>
  import { onMount } from 'svelte'
  import Button from './Button.svelte'
  import CheckBox from './CheckBox.svelte'

  let isOpen = false
  let autoPlay = false
  let closeOnLaunch = false

  onMount(async () => {
    autoPlay = await window.api.getSetting('autoPlay')
    closeOnLaunch = await window.api.getSetting('closeOnLaunch')
  })
</script>

<Button className="settings-button" label="Settings" onClick={() => (isOpen = !isOpen)} />

{#if isOpen}
  <div class="settings-modal">
    <div class="title">Settings</div>
    <div class="separator"><div></div></div>
    <div class="content">
      <CheckBox
        bind:checked={autoPlay}
        label="Auto Play"
        onChange={() => {
          window.api.setSetting('autoPlay', autoPlay)
        }}
      />
      <CheckBox
        bind:checked={closeOnLaunch}
        disabled={autoPlay}
        label="Close on Launch"
        onChange={() => {
          window.api.setSetting('closeOnLaunch', closeOnLaunch)
        }}
      />
    </div>
    <Button onClick={() => (isOpen = false)} label="Close" />
  </div>
{/if}

<style>
  :global(.settings-button) {
    font-size: 14px;
  }

  .settings-modal {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1000;

    display: flex;
    flex-direction: column;
    width: 200px;
  }

  .title {
    height: 21px;
    text-align: center;

    background-image: url('../assets/images/panel_header_bg.png');

    border: 3px solid transparent;
    border-image: url('../assets/images/panel_header_border.png') 3 repeat;
    box-sizing: border-box;
  }

  .separator {
    margin: 0 -5px;
    margin-top: -2px;
    z-index: 1;
    height: 6px;

    border-width: 2px 12px 4px 12px;
    border-style: solid;
    border-color: transparent;
    border-image: url('../assets/images/separator_border.png') 2 12 4 12 repeat;

    & > div {
      height: 6px;
      margin: 0px -5px;

      background-image: url('../assets/images/separator_bg.png');
    }
  }

  .content {
    margin-top: -5px;
    overflow-y: auto;

    background-image: url('../assets/images/window_bg.png');
    border: 4px solid transparent;
    border-image: url('../assets/images/panel_border.png') 4 repeat;
    box-sizing: border-box;

    &::-webkit-scrollbar {
      width: 4px;
    }

    &::-webkit-scrollbar-button {
      display: none;
      width: 0;
      height: 0;
    }

    &::-webkit-scrollbar-track {
      background: transparent;
    }

    &::-webkit-scrollbar-thumb {
      background: linear-gradient(180deg, #f2af4e, #ff9f18);
      border-radius: 8px;
    }
  }
</style>
