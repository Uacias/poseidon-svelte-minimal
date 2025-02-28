<script>
  import { onMount } from "svelte";

  let hashResult = "";

  async function computePoseidon() {
    const circomlibjs = await import("https://esm.sh/circomlibjs@0.1.7?bundle");

    const poseidonOpt = await circomlibjs.buildPoseidonOpt();

    const input = [1, 2];
    const hash = poseidonOpt(input);
    const hashHex = poseidonOpt.F.toString(hash);

    hashResult = `Poseidon Opt hash: ${hashHex}`;
    console.log(hashResult);
  }
</script>

<main class="container">
  <button on:click={computePoseidon}>Generate Poseidon Hash</button>
  <p>{hashResult}</p>
</main>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    margin-top: 50px;
    font-family: Arial, sans-serif;
  }

  button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }

  p {
    font-size: 18px;
    font-weight: bold;
  }
</style>
