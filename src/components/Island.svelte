<script lang="ts">
    import Mail from "../assets/mail.svg";
    import GitHub from "../assets/github.svg";
    import LinkedIn from "../assets/linkedin.svg";
    import X from "../assets/x.svg";
    import Instagram from "../assets/instagram.svg";

    type Handle = {
        name: string;
        icon: string;
        link: string;
    };

    const handles: Handle[] = [
        {
            name: "Mail",
            icon: Mail,
            link: "mailto:harshath3018@gmail.com",
        },
        {
            name: "GitHub",
            icon: GitHub,
            link: "https://github.com/TheRootDaemon",
        },
        {
            name: "LinkedIn",
            icon: LinkedIn,
            link: "https://www.linkedin.com/in/therootdaemon",
        },
        {
            name: "X",
            icon: X,
            link: "https://www.x.com/therootdaemon",
        },
        {
            name: "Instagram",
            icon: Instagram,
            link: "https://www.instagram.com/therootdaemon",
        },
    ];
</script>

<section class="social-handles">
    {#each handles as handle}
        <a
            href={handle.link}
            target="_blank"
            rel="noopener noreferrer"
            class="handle-link"
            title={handle.name}
            ><img src={handle.icon} alt={handle.name} class="icon" /></a
        >
    {/each}
</section>
