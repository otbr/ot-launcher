<script>
  import Logo from './components/Logo.svelte'
  import Socials from './components/Socials.svelte'
  import NewsPanel from './components/NewsPanel.svelte'
  import Updater from './components/Updater.svelte'
  import TopButtons from './components/TopButtons.svelte'
</script>

<Logo />
<div class="container">
  <TopButtons />
  <Socials />
  <NewsPanel />
  <Updater />
</div>

<style>
  .container {
    position: relative;
    display: flex;
    flex-direction: column;
    padding: 10px 20px;
    height: calc(100vh - var(--logo-height) + var(--logo-margin));
  }
</style>
