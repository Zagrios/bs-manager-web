<script lang="ts">
    import backgroudVideoAvc from "$lib/videos/background_video.avc.mp4"
    import { onMount } from "svelte";

    let video: HTMLVideoElement;

    onMount(() => {
        video.playbackRate = 0.75;
    });
</script>

<div class="{$$restProps.class} after:absolute after:size-full after:top-0 after:left-0 after:backdrop-blur-[80px]">
    <video bind:this={video} class="size-full object-cover" src="{backgroudVideoAvc}" autoplay loop muted defaultMuted preload="auto">
</div>
