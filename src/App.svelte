<script lang="ts">
    import Hero from "./components/Hero.svelte";
    import About from "./components/About.svelte";
    import Island from "./components/Island.svelte";
</script>

<div class="min-h-screen flex flex-col items-center justify-center">
    <div class="mb-20">
        <div
            class="flex flex-col min-[1080px]:flex-row items-center justify-center text-center min-[1000px]:text-left gap-8 min-[1000px]:gap-12 p-6 sm:p-8 md:p-12 w-full max-w-7xl mx-auto"
        >
            <Hero />
            <About />
        </div>
    </div>
    <footer>
        <Island />
    </footer>
</div>
