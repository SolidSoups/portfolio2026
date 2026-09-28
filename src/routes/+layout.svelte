<script lang="ts">
    import '../app.css';
    import '@fontsource-variable/source-serif-4';
    import '@fontsource-variable/literata';
    import '@fontsource-variable/newsreader';
    import '@fontsource-variable/inter';
    import '@fontsource-variable/ibm-plex-sans';
    import '@fontsource-variable/geist';
    import '@fontsource-variable/jetbrains-mono';
    import '@fontsource/ibm-plex-mono/400.css';
    import '@fontsource/ibm-plex-mono/700.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<main class="grid grid-cols-[minmax(0,1fr)_minmax(0,48rem)_minmax(0,1fr)] bg-paper">
    <!-- TODO: We'll need to find a better font for this -->
    <aside class="col-start-1 hidden w-64 justify-self-end pt-55 pr-16 xl:block font-serif">
        <h1 class="text-4xl pb-8">Elias Brown</h1>
        <nav class="flex flex-col gap-2">
            <a href="/">Home</a>
            <a href="/projects">Projects</a>
            <a href="about">About</a>

            <hr class="my-6 border-stone-300" />

            <address class="flex flex-col gap-1 text-sm not-italic">
                <a href="mailto:eli.marc.brown@gmail.com">eli.marc.brown@gmail.com</a>
                <a href="https://github.com/SolidSoups" target="_blank">GitHub</a>
                <a href="https://www.linkedin.com/in/elias-brown-184b86258/" target="_blank">LinkedIn</a>
            </address>
        </nav>
    </aside>

    <!-- font-serif is a great contender -->
    <!-- font-mono is a great contender for code -->
    <div class="col-start-2 min-h-screen px-12 pt-32 pb-16 lg:translate-x-12 font-serif">
        {@render children()}
    </div>
</main>

