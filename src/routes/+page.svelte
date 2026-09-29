<script>
    import ProjectCard from '$lib/components/ProjectCard.svelte'
</script>

<h1 class="max-w-[31ch] text-4xl font-bold text-blue-600">
    <u>I'm Elias</u>, a programmer alumni from FutureGames Malmö making tools and tinkering with Graphics APIs. 
</h1>
<h2 class="text-2xl font-bold text-black pl-5 pt-5">
    <span class="highlight box-decoration-clone">
        <i>I'm currently looking for work. Take a look around, then send me a message!</i>
    </span>
</h2>
<br/>
<div class="flex flex-col gap-16 pt-15">
    <ProjectCard 
        projectTitle="My internship at BitFire"
        projectDesc="Unreal tools and swarming. ;)"
    />
    <ProjectCard 
        projectTitle="Voxel Engine"
        projectDesc="Performant voxel physics simulation with OpenGL."
    />
    <ProjectCard 
        projectTitle="Sushi 2 Go"
        projectDesc="A 2-week game project combining the love of sushi with endless running."
    />
    <ProjectCard
        projectTitle="Something Cool"
    />
</div>
