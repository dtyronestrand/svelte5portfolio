<script lang="ts">
	import { page } from '$app/stores';
    import {asLink, type KeyTextField, type LinkField} from '@prismicio/client';
import {PrismicLink} from '@prismicio/svelte';
    interface Props {
        field: LinkField;
        label: KeyTextField;
        onLinkClick: (event:MouseEvent) => void;
        type: "desktop" | "mobile";
    }

    let {
        field,
        label,
        onLinkClick,
        type
    }: Props = $props();

    const path = asLink(field) ;
    let isActive = $derived(path && $page.url.pathname.includes(path));
</script>

{#if type === "desktop"}
 <PrismicLink class="group relative block overflow-hidden rounded px-3 py-1 text-base font-bold text-primary-900" {field} on:click={onLinkClick} aria-current={isActive?'page': undefined}>
        <span class={`absolute inset-0 z-0 h-full rounded bg-secondary-300 transition-transform duration-300 ease-in-out group-hover:translate-y-0 ${isActive ? `translate-y-6`: `translate-y-8`}`}></span>
        <span class="relative">{label}</span>
    </PrismicLink>
    {:else}
    <PrismicLink class="group relative block overflow-hidden rounded px-3 text-3xl font-bold text-primary-900" {field} on:click={onLinkClick} aria-current={isActive?`page`: undefined}>
        <span class={`absolute inset-0 z-0 h-full rounded bg-secondary-300 transition-transform duration-300 ease-in-out group-hover:translate-y-0 ${isActive ? `translate-y-6`: `translate-y-16`}`}></span>
        <span class="relative">{label}</span>
    </PrismicLink>
    {/if}