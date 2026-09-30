<script>
    let { 
        projectTitle = 'Project Title',
        projectDesc = 'A short description about this project, what i built and whatnot.'
    } = $props();
</script>

<div class="flex flex-col gap-4 pb-15">
    <div class="aspect-square bg-stone-300 rounded-xs"></div>

    <div class="flex flex-col gap-2">
        <h2 class="text-2xl font-bold">{projectTitle}</h2>
        <p>{projectDesc}</p>
    </div>
</div>
