<script lang="ts">
  import { twMerge } from "tailwind-merge";
  import { clsx } from "clsx";
  import type { SvelteHTMLElements } from "svelte/elements";
  let { children, ...props }: SvelteHTMLElements["main"] = $props();
</script>

<main {...props} class={twMerge("flex-grow", clsx(props.class))}>
  {@render children?.()}
</main>
