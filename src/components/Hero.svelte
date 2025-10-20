<script lang="ts">
    let profileImage = "/metaphorKeeb.png";
    let name = "Harshavardhan";
    let username = "TheRootDaemon";
</script>

<div
    class="flex flex-col items-center justify-center text-center text-[var(--fg-dawn)] font-mono p-4 sm:p-6 md:p-8 w-auto max-w-full"
>
    <img
        src={profileImage}
        alt={`${name}'s profile`}
        class="w-64 h-64 sm:w-80 sm:h-80 md:w-96 md:h-96 min-w-16 min-h-16 rounded-full object-cover hack-shadow mb-5 sm:mb-6"
    />

    <div class="space-y-2 sm:space-y-3">
        <h2 class="text-lg sm:text-xl md:text-2xl lg:text-3xl font-bold">
            {name}
        </h2>
        <p
            class="text-xl sm:text-2xl md:text-3xl lg:text-4xl font-bold font-vt323 hack-shadow"
        >
            @{username}
        </p>
    </div>
</div>
