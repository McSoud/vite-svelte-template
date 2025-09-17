<script lang="ts">
	import clsx from 'clsx';
	import type { HTMLAttributes, HTMLSelectAttributes } from 'svelte/elements';
	import { twMerge } from 'tailwind-merge';

	interface Props extends Omit<HTMLSelectAttributes, 'name' | 'title'> {
		name: string;
		title: string;
		containerClass?: HTMLAttributes<HTMLElement>['class'];
		labelClass?: HTMLAttributes<HTMLLabelElement>['class'];
		label?: HTMLLabelElement['children'] | true;
	}
	let {
		containerClass,
		labelClass,
		label,
		children,
		value = $bindable(),
		...props
	}: Props = $props();
</script>

<div class={twMerge('select-field', clsx(containerClass))}>
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
		<select id={props.name ? `${props.name}-input` : undefined} {...props} bind:value>
			{@render children?.()}
		</select>
	</div>
</div>
