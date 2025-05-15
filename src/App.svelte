<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
</script>

<main>
  <div>
    <img src={viteLogo} class="logo" alt="Vite Logo" />
    <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
  </div>
  <h1>Svelte Counter Game</h1>

  <div class="card">
    <Counter />
  </div>

  <p>
    Made with Svelte+Vite
  </p>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
</style>
