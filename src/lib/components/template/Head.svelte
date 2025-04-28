<script lang="ts">
  let { title }: { title: string } = $props();
</script>

<svelte:head>
  <title>{title} &nbsp;|&nbsp; {import.meta.env.VITE_APP_NAME}</title>
</svelte:head>
