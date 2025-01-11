<script>
  import logo from './assets/lazy_uranus.svg'
  import Panel from './lib/SwipePanel.svelte'
</script>

<main>
  <div class="logo-container">
    <a href="https://kamiviolet.site" target="_blank" rel="noreferrer">
      <img src={logo} class="logo" alt="logo" />
    </a>
  </div>
  <h1>Swipe Panel (Svelte)</h1>
  <p class="welcome-msg">
    Click on the planet to visit my website for other stuff :)
  </p>
  <Panel/>
</main>

<style>
  .logo {
    height: 8rem;
    padding: 1.25em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
