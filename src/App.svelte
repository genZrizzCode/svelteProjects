<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'

  let showAlert = false;

  function unlockAchievement() {
    showAlert = true;
    setTimeout(() => showAlert = false, 3000);
  }
</script>

<main>
  <div>
    <img src={viteLogo} class="logo" alt="Vite Logo" />
    <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
  </div>
  <h1>Svelte Counter Game</h1>

  <button on:click={unlockAchievement}>Unlock Achievement</button>

  <div class="card">
    <Counter />
  </div>

  <p>
    Made with Svelte + Vite
  </p>

  {#if showAlert}
    <div class="achievement-alert">
      🏆 Achievement unlocked!
    </div>
  {/if}
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

  .achievement-alert {
    position: fixed;
    top: 1rem;
    right: 1rem;
    background-color: #4caf50;
    color: white;
    padding: 1rem 1.5rem;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0,0,0,0.2);
    z-index: 999;
    animation: fadein 0.5s ease;
  }

  @keyframes fadein {
    from { opacity: 0; transform: translateY(-10px); }
    to   { opacity: 1; transform: translateY(0); }
  }
</style>
