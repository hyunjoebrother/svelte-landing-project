<script>
	// TailwindCSS class props
	export let primary = false;
	export let second = false;
</script>

<button
	class={`
    ${primary && 'bg-blue-500 text-white'} 
    ${second && 'border-2 border-blue-500 text-blue-500'}
    w-48 h-12 rounded-[10px] text-lg font-medium text-center cursor-pointer`}
>
		<slot />
</button>