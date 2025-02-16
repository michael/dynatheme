<script>
  let spacing_mode = $state('normal');
  let radius_multiplier = $state(1);
  let font = $state("sans");
  let theme = $state("light");

  // Update spacing variables reactively
  $effect(() => { document.documentElement.style.setProperty("--spacing", `var(--spacing-${spacing_mode})`); });
  
  // Update radius variables reactively
  $effect(() => { document.documentElement.style.setProperty("--radius-multiplier", radius_multiplier); });

  // Update font variables reactively
  $effect(() => { document.documentElement.style.setProperty("--font-family", `var(--font-${font})`); });

  // Update color variables reactively
  $effect(() => {
    document.documentElement.style.setProperty("--color-bg", `var(--color-bg-${theme})`);
    document.documentElement.style.setProperty("--color-text", `var(--color-text-${theme})`);
    document.documentElement.style.setProperty("--color-accent-1", `var(--color-accent-1-${theme})`);
  });
</script>


<!-- Hard-coded  -->
<div class="max-w-4xl w-full mx-auto px-2 py-4">

  <div class="text-xs md:text-sm overflow-auto px-1">
    <div class="flex flex-row">
      <div class="flex gap-1 py-1">
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{spacing_mode === 'tight' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => spacing_mode = "tight"}>Tight</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{spacing_mode === 'normal' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => spacing_mode = "normal"}>Normal</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{spacing_mode === 'spacious' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => spacing_mode = "spacious"}>Spacious</button>
      </div>
      <div class="flex gap-1 py-1 pl-4">
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{radius_multiplier === 0 ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => radius_multiplier = 0}>Square</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{radius_multiplier === 1 ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => radius_multiplier = 1}>Rounder</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{radius_multiplier === 2 ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => radius_multiplier = 2}>Roundest</button>
      </div>
    </div>
    <div class="flex flex-row">
      <div class="flex gap-1 py-1">
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{font === 'sans' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => font = "sans"}>Sans</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{font === 'serif' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => font = "serif"}>Serif</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{font === 'mono' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => font = "mono"}>Mono</button>
      </div>
      <div class="flex gap-1 py-1 pl-4">
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{theme === 'light' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => theme = "light"}>Light</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{theme === 'dark' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => theme = "dark"}>Dark</button>
        <button class="py-0.5 px-1 md:px-2 md:py-1 bg-accent-1 text-bg ring-offset-bg rounded{theme === 'orange' ? ' ring-accent-1 ring-2 ring-offset-1' : ''}" onclick={() => theme = "orange"}>Orange</button>
      </div>
    </div>
  </div>

  <div>
    <h1 class="text-5xl md:text-7xl tracking-tighter font-bold mt-4 mb-2">Dynamic theming with Svelte 5 & Tailwind 4</h1>
    <h2 class="text-3xl tracking-tighter font-bold mt-4 mb-2 text-accent-1">Not yet editable heading</h2>
    <p class="my-2">In a next step we'd integrate <a class="underline" href="https://svedit.vercel.app" target="_blank">Svedit</a> to make this page editable directly in the layout. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur porttitor pretium elit eget euismod. Maecenas semper euismod ex, ac pharetra tellus posuere in. Praesent finibus nec nunc vitae facilisis. Morbi vitae pulvinar nunc. Sed vitae velit aliquam, efficitur justo sed, euismod mauris. Nulla bibendum dignissim felis eu hendrerit. Quisque vel erat lacus.</p>
    <!-- Image galleary -->
    <div class={`grid ${spacing_mode === "spacious" ? "grid-cols-2 lg:grid-cols-3" : "grid-cols-2 lg:grid-cols-4"} gap-2 lg:gap-3 my-2`}>
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
      <img class="rounded-md w-full" alt="" src="https://tailwindcss.com/_next/static/media/cover.de1997f7.png" />
    </div>
    <p class="my-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur porttitor pretium elit eget euismod. Maecenas semper euismod ex, ac pharetra tellus posuere in. Praesent finibus nec nunc vitae facilisis. Morbi vitae pulvinar nunc. Sed vitae velit aliquam, efficitur justo sed, euismod mauris. Nulla bibendum dignissim felis eu hendrerit. Quisque vel erat lacus.</p>
    <h2 class="text-3xl tracking-tighter font-bold mt-4 mb-2 text-accent-1">Not yet editable heading</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur porttitor pretium elit eget euismod. Maecenas semper euismod ex, ac pharetra tellus posuere in. Praesent finibus nec nunc vitae facilisis. Morbi vitae pulvinar nunc. Sed vitae velit aliquam, efficitur justo sed, euismod mauris. Nulla bibendum dignissim felis eu hendrerit. Quisque vel erat lacus.</p>
  </div>
</div>