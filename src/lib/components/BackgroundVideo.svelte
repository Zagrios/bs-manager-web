<script lang="ts">
    import backgroudVideoAvc from "$lib/videos/background_video.mp4"
    import thumbnail from "$lib/images/video-thumnail.jpg"
</script>

<div class="{$$restProps.class} after:absolute after:size-full after:top-0 after:left-0 after:backdrop-blur-[80px]">
    <video class="size-full object-cover" src="{backgroudVideoAvc}" autoplay loop muted defaultMuted preload="auto" poster="{thumbnail}">
</div>
