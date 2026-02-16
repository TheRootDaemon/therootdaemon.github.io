<script lang="ts">
    import Email from "../assets/Email.svelte";
    import GitHub from "../assets/GitHub.svelte";
    import LinkedIn from "../assets/LinkedIn.svelte";
    import X from "../assets/X.svelte";
    import Instagram from "../assets/Instagram.svelte";
    let email = "harshath3018@gmail.com";
    let github = "TheRootDaemon";
    let linkedin = "in/therootdaemon";
    let twitter = "@therootdaemon";
    let instagram = "therootdaemon";
</script>

<footer class="w-full py-2 px-4 sm:py-4">
    <div class="max-w-3xl mx-auto">
        <div
            class="mx-auto w-fit
			       bg-(--surface) rounded-full p-2 sm:p-3 md:p-4 lg:p-5
			       shadow-xl backdrop-blur-sm
			       flex items-center gap-2 sm:gap-3 md:gap-4 lg:gap-5
			       transition-all duration-300"
        >
            <a
                href="mailto:{email}"
                class="group p-2 sm:p-2 md:p-2.5 lg:p-3 rounded-full bg-(--moon) text-(--iris)
				       transition-all duration-300
				       hover:scale-110 hover:bg-(--iris) hover:text-(--moon)
				       focus:outline-none focus:ring-2 focus:ring-(--iris)/40"
                title="Email"
            >
                <Email
                    className="w-4 h-4 sm:w-5 sm:h-5 md:w-6 md:h-6 lg:w-7 lg:h-7 xl:w-8 xl:h-8"
                />
            </a>
            <a
                href="https://github.com/{github}"
                class="group p-2 sm:p-2 md:p-2.5 lg:p-3 rounded-full bg-(--moon) text-(--iris)
				       transition-all duration-300
				       hover:scale-110 hover:bg-(--iris) hover:text-(--moon)
				       focus:outline-none focus:ring-2 focus:ring-(--iris)/40"
                title="GitHub"
            >
                <GitHub
                    className="w-4 h-4 sm:w-5 sm:h-5 md:w-6 md:h-6 lg:w-7 lg:h-7 xl:w-8 xl:h-8"
                />
            </a>
            <a
                href="https://www.linkedin.com/{linkedin}"
                class="group p-2 sm:p-2 md:p-2.5 lg:p-3 rounded-full bg-(--moon) text-(--iris)
				       transition-all duration-300
				       hover:scale-110 hover:bg-(--iris) hover:text-(--moon)
				       focus:outline-none focus:ring-2 focus:ring-(--iris)/40"
                title="LinkedIn"
            >
                <LinkedIn
                    className="w-4 h-4 sm:w-5 sm:h-5 md:w-6 md:h-6 lg:w-7 lg:h-7 xl:w-8 xl:h-8"
                />
            </a>
            <a
                href="https://twitter.com/{twitter.replace('@', '')}"
                class="group p-2 sm:p-2 md:p-2.5 lg:p-3 rounded-full bg-(--moon) text-(--iris)
				       transition-all duration-300
				       hover:scale-110 hover:bg-(--iris) hover:text-(--moon)
				       focus:outline-none focus:ring-2 focus:ring-(--iris)/40"
                title="X / Twitter"
            >
                <X
                    className="w-4 h-4 sm:w-5 sm:h-5 md:w-6 md:h-6 lg:w-7 lg:h-7 xl:w-8 xl:h-8"
                />
            </a>
            <a
                href="https://instagram.com/{instagram}"
                class="group p-2 sm:p-2 md:p-2.5 lg:p-3 rounded-full bg-(--moon) text-(--iris)
				       transition-all duration-300
				       hover:scale-110 hover:bg-(--iris) hover:text-(--moon)
				       focus:outline-none focus:ring-2 focus:ring-(--iris)/40"
                title="Instagram"
            >
                <Instagram
                    className="w-4 h-4 sm:w-5 sm:h-5 md:w-6 md:h-6 lg:w-7 lg:h-7 xl:w-8 xl:h-8"
                />
            </a>
        </div>
    </div>
</footer>
