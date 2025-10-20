<script lang="ts">
    import Hero from "./components/Hero.svelte";
    import About from "./components/About.svelte";
</script>

<div class="min-h-screen flex items-center justify-center">
    <div
        class="flex flex-col md:flex-row items-center justify-center text-center md:text-left gap-8 md:gap-12 p-6 sm:p-8 md:p-12 w-full max-w-7xl mx-auto"
    >
        <Hero />
        <About />
    </div>
</div>
