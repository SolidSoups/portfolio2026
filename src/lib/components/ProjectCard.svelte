<script>
    let { 
        projectTitle = 'Project Title',
        projectDesc = 'A short description about this project, what i built and whatnot.'
    } = $props();
</script>

<div class="grid grid-cols-2 gap-8">
    <div class="aspect-[4/3] bg-stone-300"></div>

    <div class="flex flex-col gap-3 pl-4">
        <h2 class="text-2xl font-bold">{projectTitle}</h2>
        <p>{projectDesc}</p>
    </div>
</div>
