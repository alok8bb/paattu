<script>
  import { fade } from "svelte/transition";
  import { BiggerPlayerVisible, active, paused } from "$lib/store";

  import Seekbar2 from "./Seekbar2.svelte";
  import Play from "$lib/icons/Play.svelte";
  import Pause from "$lib/icons/Pause.svelte";
  import Prev from "$lib/icons/Prev.svelte";
  import Next from "$lib/icons/Next.svelte";
  import Lyrics from "./Lyrics.svelte";
  import CurrentPlaylist from "./CurrentPlaylist.svelte";
  import Repeat from '$lib/icons/Repeat.svelte'
  import Shuffle from '$lib/icons/Shuffle.svelte'
  import Volume from '$lib/components/Volume.svelte'

  function close(e) {
    if (e.key === "Escape") {
      $BiggerPlayerVisible = false;
    }
  }

  let shown = CurrentPlaylist;
</script>

<div class="biggerplayer flex flex-ac flex-jc flex-dirc" transition:fade>
  <div class="player_container flex">
    <div class="player flex flex-jc flex-ac flex-dirc">
      <img
        src={$active.image.replace("150x150", "500x500")}
        alt={$active.title}
        loading="lazy"
      />

      <div class="info_container">
        <div class="title">{@html $active.title}</div>
        <div class="subtitle">{@html $active.subtitle.split("-")[0]}</div>
        <div class="album">{@html $active.more_info.album}</div>
      </div>

      <div class="seekbar_container">
        <Seekbar2 />
      </div>

      <div class="buttons flex flex-ac flex-jc">
        <Repeat />

        <Prev />

        {#if $paused}
          <Play />
        {:else}
          <Pause />
        {/if}

        <Next />

        <Shuffle />
        <Volume />
      </div>
    </div>

    <div class="lyrics_playlist flex flex-dirc">
      <div class="lyrplaybtns flex">
        <button
          class:colorful={shown === Lyrics}
          on:click={() => (shown = Lyrics)}>Lyrics</button
        >

        <button
          on:click={() => (shown = CurrentPlaylist)}
          class:colorful={shown === CurrentPlaylist}>Now Playing</button
        >
      </div>

      {#key shown}
        <svelte:component this={shown} />
      {/key}
    </div>
  </div>

  <button class="close glow" on:click={() => ($BiggerPlayerVisible = !$BiggerPlayerVisible)}>✕</button>
</div>

<svelte:window on:keydown={close} />

<style>
  div.biggerplayer {
    position: fixed;
    top: 0;
    left: 0;
    height: 100dvh;
    width: 100dvw;
    gap: 1rem;
    background-color: #0000008e;
    backdrop-filter: blur(13.6px);
    -webkit-backdrop-filter: blur(13.6px);
  }
  div.player_container {
    height: 100dvh;
    width: 96%;
    max-width: 1800px;
  }
  div.player {
    gap: 1rem;
  }
  div.title {
    margin-top: 0.5rem;
    font-weight: bold;
  }
  div.subtitle,
  div.album {
    font-size: 0.8rem;
  }
  img {
    border-radius: 0.3rem;
  }
  @media (max-width: 1000px) {
    img {
      height: 50%;
    }
    .player_container {
      padding: 2rem 0;
      flex-direction: column;
      gap: 2rem;
    }
    .player {
      height: 40%;
    }
    .lyrplaybtns {
      text-align: center;
    }
  }
  @media (min-width: 1000px) {
    img {
      width: 50%;
    }
    .player {
      width: 50%;
    }
  }
  button.close {
    all: unset;
    position: fixed;
    top: 1.5rem;
    left: 1.5rem;
    cursor: pointer;
    font-size: 1.5rem;
  }
  .seekbar_container {
    width: 80%;
  }
  div.info_container {
    text-align: center;
    width: 100%;
  }
  div.lyrics_playlist {
    gap: 0.5rem;
  }
  @media (max-width: 1000px) {
    div.lyrics_playlist {
      height: 60%;
    }
  }
  @media (min-width: 1000px) {
    div.lyrics_playlist {
      width: 50%;
      margin: 2rem 0;
    }
  }
  .buttons {
    width: 80%;
    justify-content: space-between;
  }
  .lyrplaybtns {
    justify-content: space-between;
  }
  .lyrplaybtns button {
    cursor: pointer;
    border: 0;
    background-color: transparent;
    color: var(--fg);
    font-weight: bold;
    transition: all 0.3s;
  }
  .colorful {
    background-image: linear-gradient(to right, #5d26c1, #a17fe0, #59c173);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent !important;
  }
</style>
