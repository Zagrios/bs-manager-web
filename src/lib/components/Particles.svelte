
<script lang="ts">
    import Particles, { particlesInit } from '@tsparticles/svelte';
    import type { IOptions } from '@tsparticles/engine';
    import { loadSlim } from '@tsparticles/slim';
    import { onMount } from 'svelte';
    import beatRunning from '$lib/images/beat_running.gif';
    import beatImpatient from '$lib/images/beat_impatient.gif';

    type RecursivePartial<T> = {
    [P in keyof T]?:
        T[P] extends (infer U)[] ? RecursivePartial<U>[] :
        T[P] extends object | undefined ? RecursivePartial<T[P]> :
        T[P];
    };

    let ParticlesComponent: typeof Particles;

    onMount(async () => {
		const module = await import('@tsparticles/svelte');
		ParticlesComponent = module.default;
	});

    const particlesConfig: RecursivePartial<IOptions> = {
        particles: {
            color: { value: "#fff" },
            move: {
                direction: "bottom",
                enable: true,
                outModes: "out",
                speed: 2
            },
            number: {
                density: {
                    enable: true,
                },
                value: 10
            },
            opacity: {
                value: 1
            },
            shape: {
                type: "image",
                options: {
                    image: [
                        { name: "beatRunningA", src: beatImpatient, gif: true },
                        { name: "beatRunning", src: beatRunning, gif: true },
                    ]
                }
            },
            size: {
                value: 25
            },
            wobble: {
                enable: true,
                distance: 10,
                speed: 10
            },
            zIndex: {
                value: { min: 0, max: 100 }
            },
        },
    };

    void particlesInit(async (engine) => {
		await loadSlim(engine);
	});

</script>

<svelte:component
    this="{ParticlesComponent}"
    id="tsparticles"
    class="{$$restProps.class}"
    options="{particlesConfig}"
/>