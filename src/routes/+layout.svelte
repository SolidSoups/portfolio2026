<script lang="ts">
    import { page } from '$app/state';
    import { beforeNavigate, afterNavigate, onNavigate }  from '$app/navigation';
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

    const links = [
        { href: '/', label: 'Home' },
        { href: '/projects', label: 'Projects' },
        { href: '/about', label: 'About' },
    ];

    const isCurrent = (href: string) => 
        href === '/' ? page.url.pathname === '/' : page.url.pathname.startsWith(href);

    // Remove smooth scrolling when switching pages
    beforeNavigate(() => {
        document.documentElement.style.scrollBehavior = 'auto';
    });
    afterNavigate(() => {
        document.documentElement.style.scrollBehavior = '';
    });

    // Add smooth animation transition between pages
    onNavigate((navigation) => {
        if(!document.startViewTransition) return;

        return new Promise((resolve) => {
            document.startViewTransition(async () => { 
                resolve();
                await navigation.complete;
            });
        });
    });
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<main class="grid grid-cols-[minmax(0,1.4fr)_minmax(0,48rem)_minmax(0,1fr)] bg-paper">
    <!-- TODO: We'll need to find a better font for this -->
    <aside class="col-start-1 hidden w-64 justify-self-end pt-55 pr-16 xl:block font-serif">
        <h1 class="text-4xl pb-8">Elias Brown</h1>
        <nav class="flex flex-col gap-2">
            {#each links as link}
                <a href={link.href} aria-current={isCurrent(link.href) ? 'page' : undefined} 
                    class="mx-1 w-fit px-0.5 aria-[current=page]:highlight">
                    {link.label}
                </a>
            {/each}

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

    <!-- The main content layout -->
    <div style="view-transition-name: content" class="col-start-2 flex min-h-screen flex-col px-12 pt-32 pb-16 lg:translate-x-12 font-serif"> 
        {@render children()}

        <footer class="mt-auto pt-16 text-sm text-stone-500">
            © {new Date().getFullYear()} Elias Brown
        </footer>
    </div>

</main>

