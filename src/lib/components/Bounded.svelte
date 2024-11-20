<!-- @migration-task Error while migrating Svelte code: $$props is used together with named props in a way that cannot be automatically migrated. -->
<script lang="ts">
import clsx from 'clsx';
    export let tag = "section";

</script>

<svelte:element this= {tag} {... $$restProps} class={clsx(`px-4 py-10 md:px-6 md:py-14 lg:py-16`,$$props.class)}>
<div class="mx-auto w-full max-w-7xl"><slot /></div>
</svelte:element>