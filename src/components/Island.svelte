<script lang="ts">
    import Email from "../assets/Email.svelte";
    import GitHub from "../assets/GitHub.svelte";
    import LinkedIn from "../assets/LinkedIn.svelte";
    import X from "../assets/X.svelte";
    import Instagram from "../assets/Instagram.svelte";

    let profileImage = "/metaphorKeeb.png";
    let name = "Harshavardhan";
    let username = "TheRootDaemon";
    let bio = "Trying to be a better Nerd, Everyday...";
    let email = "harshath3018@gmail.com";
    let github = "TheRootDaemon";
    let linkedin = "in/therootdaemon";
    let twitter = "@therootdaemon";
    let instagram = "therootdaemon";
</script>

<div
    class="border font-mono text-[var(--fg-dawn)] w-full max-w-xs sm:max-w-sm md:max-w-md lg:max-w-lg"
>
    <div class="flex justify-center mb-4 hack-shadow">
        <img
            src={profileImage}
            alt={`${name}'s profile`}
            class="w-32 h-32 sm:w-40 sm:h-40 md:w-48 md:h-48 rounded-full object-cover"
        />
    </div>

    <!-- Name Section -->
    <div class="text-center mb-4">
        <h2 class="text-xl sm:text-2xl font-bold">{name}</h2>
        <p class="text-lg sm:text-xl">{username}</p>
    </div>

    <!-- Bio Section -->
    <div class="mb-4">
        <p class="text-sm sm:text-base">
            {bio}
        </p>
    </div>

    <div class="space-y-3">
        <div class="flex items-center gap-2 text-sm sm:text-base">
            <Email className="hack-shadow text-[var(--fg-dawn)]" />
            <a href="mailto:harshath3018@gmail.com">{email}</a>
        </div>

        <div class="flex items-center gap-2 text-sm sm:text-base">
            <GitHub className="hack-shadow text-[var(--fg-dawn)]" />
            <a href="https://github.com/{github}">{github}</a>
        </div>

        <div class="flex items-center gap-2 text-sm sm:text-base">
            <LinkedIn className="hack-shadow text-[var(--fg-dawn)]" />
            <a href="https://www.linkedin.com/{linkedin}">{linkedin}</a>
        </div>

        <div class="flex items-center gap-2 text-sm sm:text-base">
            <X className="hack-shadow text-[var(--fg-dawn)]" />
            <a href="https://twitter.com/{twitter.replace('@', '')}"
                >{twitter}</a
            >
        </div>

        <div class="flex items-center gap-2 text-sm sm:text-base">
            <Instagram className="hack-shadow text-[var(--fg-dawn)]" />
            <a href="https://instagram.com/{instagram}">{instagram}</a>
        </div>
    </div>
</div>
