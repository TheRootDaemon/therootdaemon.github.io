<script lang="ts">
    let profileImage = "/metaphorKeeb.png";
    let name = "Harshavardhan";
    let username = "TheRootDaemon";
</script>

<div class="p-4 sm:p-6 md:p-8">
    <div class="flex items-center space-x-4 sm:hidden">
        <img
            src={profileImage}
            alt={`${name}'s profile`}
            class="w-16 h-16 min-w-16 min-h-16 aspect-square rounded-full object-cover hack-shadow flex-shrink-0"
        />
        <div class="space-y-1 text-left">
            <h2 class="text-lg font-mono text-[var(--fg-dawn)]">
                {name}
            </h2>
            <p
                class="text-xl font-bold font-vt323 text-[var(--fg-dawn)] hack-shadow"
            >
                @{username}
            </p>
        </div>
    </div>

    <div
        class="hidden sm:flex flex-col items-center justify-center text-center text-[var(--fg-dawn)] font-mono"
    >
        <img
            src={profileImage}
            alt={`${name}'s profile`}
            class="w-64 h-64 sm:w-80 sm:h-80 md:w-96 md:h-96 min-w-16 min-h-16 aspect-square rounded-full object-cover hack-shadow mb-5 sm:mb-6"
        />
        <div class="space-y-2 sm:space-y-3">
            <h2 class="text-lg sm:text-xl md:text-2xl lg:text-3xl">
                {name}
            </h2>
            <p
                class="text-xl sm:text-2xl md:text-3xl lg:text-4xl font-bold font-vt323 hack-shadow"
            >
                @{username}
            </p>
        </div>
    </div>
</div>
