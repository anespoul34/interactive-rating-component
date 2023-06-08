<script lang="ts">

  let ranked: boolean = false;
  let selected: number = 3;

  function handleSelection(value: number) {
    selected = value;
  }

  function submitRanking() {
    if (!selected) return;
    ranked = true;
  }
</script>

<main class={ranked ? 'ranked' : ''}>
  {#if !ranked}
    <div class="icon">
      <img src="./assets/images/icon-star.svg" alt="star icon">
    </div>
    <h1>How did we do ?</h1>
    <p class="description">Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!</p>
    <form on:submit|preventDefault={submitRanking}>
      <div class="inputs-container">
        <input class={selected === 1 ? 'selected' : '' } type="button" value="1" on:click={() => { handleSelection(1) }}>
        <input class={selected === 2 ? 'selected' : '' } type="button" value="2" on:click={() => { handleSelection(2) }}>
        <input class={selected === 3 ? 'selected' : '' } type="button" value="3" on:click={() => { handleSelection(3) }}>
        <input class={selected === 4 ? 'selected' : '' } type="button" value="4" on:click={() => { handleSelection(4) }}>
        <input class={selected === 5 ? 'selected' : '' } type="button" value="5" on:click={() => { handleSelection(5) }}>
      </div>
      <button type="submit">SUBMIT</button>
    </form>
  {:else}
    <img src="./assets/images/illustration-thank-you.svg" alt="thanks illustration">
    <div class="results-info">
      <p>You selected {selected} out of 5</p>
    </div>
    <h1>Thank you!</h1>
    <p class="appreciation">We appreciate you taking the time to give a rating. If you ever need more support, don't hesitate to get in touch!</p>
  {/if}
  

</main>
<footer class="attribution">
  Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
  Coded by <a href="https://www.arthurnespoulous.com" target="_blank">AN</a>.
</footer>

<style lang="scss">
  main {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    width: 360px;
    height: 360px;
    border-radius: 15px;
    padding: 26px;

    .icon {
      width: 46px;
      height: 46px;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 23px;
      background-color: hsla(216, 12%, 54%, 0.1);
    }

    .description {
      line-height: 1.4;
    }
    .appreciation {
      line-height: 1.4;
      text-align: center;
    }

    form {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;

      .inputs-container {
        width: 100%;
        display: flex;
        justify-content: space-between;
      }
      button {
        margin-top: 26px;
      }
    }
  }
  .ranked {
    align-items: center;

    .results-info {
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: hsla(216, 12%, 54%, 0.1);
      padding: 0 16px;
      height: 40px;
      border-radius: 20px;

      p {
        margin-top: 4px;
        color: hsla(25, 97%, 53%, 0.7);
      }
    }
  }

  @media screen and (min-width: 768px) {
    main {
      width: 400px;
      height: 400px;
      padding: 30px;
    }
  }
</style>