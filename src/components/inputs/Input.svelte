<script lang="ts">
	import clsx from 'clsx';
	import type { Component } from 'svelte';
	import type {
		HTMLAttributes,
		HTMLInputAttributes,
		HTMLInputTypeAttribute,
		SVGAttributes
	} from 'svelte/elements';
	import { twMerge } from 'tailwind-merge';

	interface Props extends Omit<HTMLInputAttributes, 'name' | 'title' | 'type'> {
		name: string;
		title: string;
		type: Exclude<HTMLInputTypeAttribute, 'checkbox' | 'hidden' | 'radio'>;
		containerClass?: HTMLAttributes<HTMLElement>['class'];
		labelClass?: HTMLAttributes<HTMLLabelElement>['class'];
		label?: HTMLLabelElement['children'] | true;
		Icon?: Component<SVGAttributes<SVGSVGElement>>;
	}
	let {
		containerClass,
		labelClass,
		label,
		type,
		Icon,
		value = $bindable(),
		...props
	}: Props = $props();
</script>

<div class={twMerge('input-field', clsx(containerClass))}>
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
		<input
			id={props.name ? `${props.name}-input` : undefined}
			{...props}
			bind:value
			type={type as HTMLInputTypeAttribute}
		/>
		{#if Icon}
			<Icon />
		{/if}
	</div>
</div>
