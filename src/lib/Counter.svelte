<script>
  import { get } from 'svelte/store';
  import { increaseAmountClicks, increaseAmountAutoClicks } from './stores.js';
  let incrementAmount = $state(1);
  let increaseAutoAmount = $state(5);
  let count = $state(0);
  let clickCost = $state(15);
  let autoCost = $state(25);
  let autoCountStarted = $state(false);

  const increment = () => {
    count += incrementAmount;
  };

  const boostIncrement = () => {
    if (count >= clickCost) {
      count -= clickCost
      if (get(increaseAmountClicks) === 1) {
        incrementAmount += 9;
      } else {
        incrementAmount += 10;
      }
      increaseAmountClicks.update(n => n + 1);
      clickCost *= 5;
    };
  };
  const startAutoCount = () => {
    if (count >= autoCost) {
      setInterval(() => {
        count += increaseAutoAmount;
      }, 1000);
      autoCountStarted = true;
    };
  };

  const upgradeAutoCount = () => {
    if (count >= autoCost) {
      count -= autoCost;
      increaseAutoAmount += 5;
      increaseAmountAutoClicks.update(n => n + 1);
      autoCost *= 7;
    }
  };
</script>

<button onclick={increment}>
  Count is {count}
</button>
<br>
<button onclick={boostIncrement}>
  Increase Increment (Now: {incrementAmount})
</button>
<br>
<h4>Cost of next click upgrade: {clickCost}</h4>
<br><br>
{#if incrementAmount >= 40 && autoCountStarted === false}
  <button onclick={startAutoCount}>
    Start Auto Count +{increaseAutoAmount}/sec (costs 40)
  </button>
  <br>
{/if}
{#if autoCountStarted}
  <button onclick={upgradeAutoCount}>
    Upgrade Auto Count (Now: +{increaseAutoAmount}/sec)
  </button>
  <br>
  <h4>Cost of next Auto Upgrade: {autoCost}</h4>
  <br><br>
{/if}