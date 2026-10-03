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
    import githubIcon from '$lib/assets/github.svg';
    import linkedinIcon from '$lib/assets/linkedin.svg';

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
        document.documentElement.style.scrollBehavior = 'auto';
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

<main class="grid min-h-screen grid-cols-[minmax(0,1.4fr)_minmax(0,72rem)_minmax(0,1fr)] grid-rows-[1fr_auto] bg-paper">
    <!-- TODO: We'll need to find a better font for this -->
    <aside class="col-start-1 row-start-1 hidden w-64 justify-self-end pt-55 pr-16 xl:block font-serif">
        <h1 class="text-4xl pb-8">Elias Brown</h1>
        <nav class="flex flex-col gap-2">
            {#each links as link}
                <a href={link.href} aria-current={isCurrent(link.href) ? 'page' : undefined} 
                    class="mx-1 w-fit px-0.5 aria-[current=page]:highlight">
                    {link.label}
                </a>
            {/each}

            <hr class="my-6 border-stone-400" />

            <address class="flex flex-col gap-2 text-sm not-italic">
                <a href="mailto:eli.marc.brown@gmail.com">Eli.marc.brown@gmail.com</a>
                <div class="flex flex-row gap-4 pt-2">
                    <a href="https://github.com/SolidSoups" target="_blank" aria-label="GitHub">
                        <img src={githubIcon} alt="" class="size-8" />
                    </a>
                    <a href="https://www.linkedin.com/in/elias-brown-184b86258/" target="_blank" aria-label="LinkedIn">
                        <img src={linkedinIcon} alt="" class="size-8" />
                    </a>
                </div>
            </address>


        </nav>
    </aside>

    <!-- font-serif is a great contender -->
    <!-- font-mono is a great contender for code -->

    <!-- The main content layout -->
    <div class="col-start-2 row-start-1 flex flex-col px-12 pt-32 pb-16 lg:translate-x-12 font-serif"> 
        <div style="view-transition-name: content">
            {@render children()}
        </div>
    </div>

    <footer style="view-transition-name: footer" class="col-start-1 col-span-2 row-start-2 grid grid-cols-subgrid items-center pb-16 text-sm text-stone-500 font-serif">
        <p class="col-start-1 hidden w-64 justify-self-end pr-16 xl:block">
            © {new Date().getFullYear()} Elias Brown
        </p>

        <div class="col-start-2 flex justify-end gap-4 px-12 lg:translate-x-12">
            <a href="https://github.com/SolidSoups" target="_blank" aria-label="GitHub">
                <img src={githubIcon} alt="" class="size-5" />
            </a>
            <a href="https://www.linkedin.com/in/elias-brown-184b86258/" target="_blank" aria-label="LinkedIn">
                <img src={linkedinIcon} alt="" class="size-5" />
            </a>
        </div>
    </footer>
</main>

