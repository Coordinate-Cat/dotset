<script>
// https://github.com/ghostdevv/svelte-copy
import { copy } from 'svelte-copy';

let copied = ``;
const copyTxt = {
hackingMachine: `macOS Monterey ver 12.5.1
MacBook Pro (13-inch, 2017, Two Thunderbolt 3 ports)
2.3GHz DualCore IntelCore i5
16GB 2133 MHz LPDDR3
Intel Iris Plus Graphics 640 1536MB
`,

nixOne: `sh <(curl -L https://nixos.org/nix/install)`,
nixTwo: `nix-shell -p nix-info --run "nix-info -m"`,

nixError: `sh <(curl -L https://nixos.org/nix/install)`,
}

</script>

<svelte:head>
	<title>dotset</title>
	<meta name="description" content="" />
	<link rel="stylesheet" href="https://unpkg.com/mono-icons@1.0.5/iconfont/icons.css">
</svelte:head>

<!-- first section -->
<section class="section_first">
	<h2>Hacking Machine</h2>
	<div class="details">
		<pre>{copyTxt.hackingMachine}</pre>
		<button use:copy={copyTxt.hackingMachine} on:svelte-copy={() => copied = copyTxt.hackingMachine }>
			<!-- check copy -->
			{#if copied === copyTxt.hackingMachine}
				<i class="mi mi-clipboard-check"><span class="u-sr-only"></span></i>
			{:else}
				<span>Copy</span>
			{/if}
		</button>
	</div>
</section>
<!-- first section -->

<!-- second section -->
<section class="section_second">
	<h2>Nix</h2>

	<div class="details">
		<pre>{copyTxt.nixOne}</pre>
		<button use:copy={copyTxt.nixOne} on:svelte-copy={() => copied = copyTxt.nixOne }>
			<!-- check copy -->
			{#if copied === copyTxt.nixOne}
				<i class="mi mi-clipboard-check"><span class="u-sr-only"></span></i>
			{:else}
				<span>Copy</span>
			{/if}
		</button>
	</div>

	<p>Quit Terminal</p>

	<div class="details">
		<pre>{copyTxt.nixTwo}</pre>
		<button use:copy={copyTxt.nixTwo} on:svelte-copy={() => copied = copyTxt.nixTwo }>
			<!-- check copy -->
			{#if copied === copyTxt.nixTwo}
				<i class="mi mi-clipboard-check"><span class="u-sr-only"></span></i>
			{:else}
				<span>Copy</span>
			{/if}
		</button>
	</div>

	<h3>Error</h3>
	<code>{copyTxt.nixError}</code>
	<p>When the above is executed...</p>
</section>
<!-- second section -->

<!-- third section -->
<section class="section_third">
	<h2>Home-manager</h2>
</section>
<!-- third section -->

<style lang="scss">
$section-pad: 10px 20px;
.section{
	&_first {
		padding: $section-pad;
		background-color: var(--firstly-color);
	}
	&_second {
		padding: $section-pad;
		background-color: var(--secondary-color);
	}
	&_third {
		padding: $section-pad;
		background-color: var(--tertiary-color);
	}
}

.details {
	position: relative;
	button {
		position: absolute;
		top: 0;
		right: 0;
	}
}

button {
	border: none;
	cursor: pointer;
	font-weight: 600;
	width: 68px;
	height: 100%;
	padding: 4px 10px;
	margin: 0;
	box-sizing: border-box;
	color: var(--sub-color);
	border: 4px solid var(--main-color);
	background-color: var(--main-color);
	&:hover {
		box-sizing: border-box;
		color: var(--main-color);
		background-color: var(--sub-color);
	}
}
</style>
