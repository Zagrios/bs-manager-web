<script lang="ts">
	import backgroudVideo from "$lib/videos/background_video.av1.mp4"
    import { onMount } from "svelte";

    let video: HTMLVideoElement;

    onMount(() => {
        video.playbackRate = 0.75;
    });
</script>

<div class="{$$restProps.class} after:absolute after:size-full after:top-0 after:left-0 after:backdrop-blur-[80px]">
    <video bind:this={video} class="size-full object-cover" src={backgroudVideo} autoplay muted loop></video>
</div>
