<script>
	export let state = 'default';
	/* export let state = 'hidden'; */
	export let showLabel = false;
	export let label = 'Status…';

	export let id = undefined;
	export let style = undefined;

	let opacityStyle = ['15%', '27%', '39%', '51%', '63%', '75%', '87%', '100%'];

	let displayStyle = 'flex';

	$: {
		if (state === 'default') {
			displayStyle = 'flex';
		} else {
			displayStyle = 'none';
		}
	}
</script>

<div class="progress-indicator" {id} style="{style}; display: {displayStyle}">
	<div class="spinner">
		<div class="container">
			<div class="vertical">
				<div class="rect-vertical" style="opacity: {opacityStyle[0]}" />
				<div class="rect-vertical" style="opacity: {opacityStyle[4]}" />
			</div>
			<div class="horizontal">
				<div class="rect-horizontal" style="opacity: {opacityStyle[6]}" />
				<div class="rect-horizontal" style="opacity: {opacityStyle[2]}" />
			</div>
		</div>
		<div class="container rotated">
			<div class="vertical">
				<div class="rect-vertical" style="opacity: {opacityStyle[1]}" />
				<div class="rect-vertical" style="opacity: {opacityStyle[5]}" />
			</div>
			<div class="horizontal">
				<div class="rect-horizontal" style="opacity: {opacityStyle[7]}" />
				<div class="rect-horizontal" style="opacity: {opacityStyle[3]}" />
			</div>
		</div>
	</div>
	{#if showLabel}
		<p>{label}</p>
	{/if}
</div>

<style>
	.progress-indicator {
		align-items: center;
		display: flex;
		gap: 8px;
		height: 22px;
		padding-left: 22px;
		position: relative;
	}

	p {
		color: var(--labels-secondary);
		font-size: 17px;
		font-weight: 400;
		line-height: 22px;
	}

	.container {
		align-items: center;
		animation: 1s rotate infinite steps(1, end);
		display: flex;
		height: 22px;
		justify-content: center;
		left: 0px;
		position: absolute;
		top: 0px;
		width: 22px;
	}

	.vertical {
		display: flex;
		flex-direction: column;
		height: 22px;
		justify-content: space-between;
	}

	.horizontal {
		display: flex;
		justify-content: space-between;
		position: absolute;
		width: 22px;
	}

	.rect-vertical {
		background: var(--labels-secondary);
		border-radius: 1.5px;
		height: 7px;
		width: 3px;
	}

	.rect-horizontal {
		background: var(--labels-secondary);
		border-radius: 1.5px;
		height: 3px;
		width: 7px;
	}

	.rotated {
		rotate: 45deg;
	}

	@keyframes rotate {
		0% {
			transform: rotate(45deg);
		}

		12.5% {
			transform: rotate(90deg);
		}

		25% {
			transform: rotate(135deg);
		}

		37.5% {
			transform: rotate(180deg);
		}

		50% {
			transform: rotate(225deg);
		}

		62.5% {
			transform: rotate(270deg);
		}

		75% {
			transform: rotate(315deg);
		}

		87.5% {
			transform: rotate(360deg);
		}

		100% {
			transform: rotate(0deg);
		}
	}
</style>
