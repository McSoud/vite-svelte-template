<script lang="ts">
	import type { Component } from 'svelte';
	import type { HTMLTextareaAttributes, SVGAttributes } from 'svelte/elements';
	import { twMerge } from 'tailwind-merge';

	interface Props extends Omit<HTMLTextareaAttributes, 'name' | 'title'> {
		name: string;
		title: string;
		containerClass?: HTMLElement['className'];
		labelClass?: HTMLElement['className'];
		label?: HTMLLabelElement['children'] | true;
		Icon?: Component<SVGAttributes<SVGSVGElement>>;
	}
	let { containerClass, labelClass, label, Icon, ...props }: Props = $props();
</script>

<div class={twMerge('textarea-field', containerClass)}>
	<label
		hidden={!label}
		for={props.id ?? (props.name ? `${props.name}-input` : undefined)}
		class={labelClass}
	>
		{label === true ? props.title : label}
		{#if props.required && label}
			<span class="required">&nbsp;*</span>
		{/if}
	</label>
	<div class="input-container">
		<textarea id={props.name ? `${props.name}-input` : undefined} {...props}></textarea>
		{#if Icon}
			<Icon />
		{/if}
	</div>
</div>
