<script>

  export let dryMp3Url;
  export let wetMp3Url;

  let dryPlayer, wetPlayer;

  let isPlaying = false;
  let wetDryVal = 0;

  function playPause() {
    isPlaying = !isPlaying;
    if(isPlaying) {
      dryPlayer.play();
      wetPlayer.play();

      dryPlayer.volume = wetDryVal;
      wetPlayer.volume = 1.0 - wetDryVal;
    }
    else {
      dryPlayer.pause();
      wetPlayer.pause();
    }
  }

  function changeWetDry() {
    dryPlayer.volume = wetDryVal;
    wetPlayer.volume = 1.0 - wetDryVal;
  }

</script>

<div class="DryWetPlayer">

  <audio preload class="DryPlayer" bind:this={dryPlayer}>
    <source src={dryMp3Url} type="audio/mpeg">
  </audio>

  <audio preload class="WetPlayer" bind:this={wetPlayer}>
    <source src={wetMp3Url} type="audio/mpeg">
  </audio>

  <div class="PlayPauseButton">
    <div class="Button" class:isPlaying on:click={playPause}></div>
  </div>

  <div class="Slider">
    <p class="DryLabel">DRY</p>
    <input type="range" min="0" max="1" bind:value={wetDryVal} on:input={changeWetDry} step="0.01">
    <p class="DryLabel">WET</p>
  </div>

</div>

<style>

  .Slider {
    margin: 0;
    padding: 0 0 0 12px;
    flex-grow: 1;
    display: flex;
  }

  .Slider p {
    font-size: 12px;
    font-weight: bold;
    padding: 0 12px;
  }

  .Slider input {
    margin: 0;
    padding: 0;
    flex-grow: 1;
    display: block;
  }

  .DryWetPlayer {
    display: flex;
    padding: 12px;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    border: 1px solid #ccc;
    max-width: 480px;
    background: #fafafa;
    margin-bottom: 12px;
  }

  audio {
    display: none;
  }

  .PlayPauseButton .Button {
    display: block;
    box-sizing: border-box;
    width: 0;
    height: 37px;
    cursor: pointer;
    border-color: transparent transparent transparent #202020;
    transition: 100ms all ease;
    border-style: solid;
    border-width: 19px 0 19px 30px;
  }
  .PlayPauseButton .Button.isPlaying {
    border-style: double;
    border-width: 0px 0 0px 30px;
  }

</style>