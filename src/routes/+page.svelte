<script>
	import Countdown from 'svelte-countdown/src/index.js';
</script>

<Countdown
	from="2023-11-17 15:00:00"
	dateFormat="YYYY-MM-DD H:m:s"
	zone="Europe/Athens"
	let:remaining
>
	<div class="countdown">
		{#if remaining.done === false}
			<div class="ymd countdown-text">
				{#if remaining.years > 0}
					<span class="years">{remaining.years} years</span>
				{/if}
				{#if remaining.months > 0}
					<span class="months">{remaining.months} months</span>
				{/if}
				<span class="days">{remaining.days} days</span>
			</div>
			<div class="time countdown-text">
				{remaining.hours}:{remaining.minutes.toString().padStart(2, '0')}:{remaining.seconds
					.toString()
					.padStart(2, '0')}
			</div>
		{:else}
			<span class="countdown-text">The time has come!</span>
		{/if}
	</div>
</Countdown>

<style>
	.countdown {
		margin-top: 20%;
		text-align: center;
		font-family: ArcaneNine;
		font-size: 10em;
	}

	.countdown-text {
		background: linear-gradient(
			to bottom,
			#cfc09f 22%,
			#634f2c 24%,
			#cfc09f 26%,
			#cfc09f 27%,
			#ffecb3 40%,
			#3a2c0f 78%
		);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		color: #fff;
		position: relative;
		text-transform: uppercase;
		margin: 0;
		font-weight: 400;
	}

	.countdown-text:after {
		background: none;
		content: attr(data-heading);
		left: 0;
		top: 0;
		z-index: -1;
		position: absolute;
		text-shadow: -1px 0 1px #c6bb9f, 0 1px 1px #c6bb9f, 5px 5px 10px rgba(0, 0, 0, 0.4),
			-5px -5px 10px rgba(0, 0, 0, 0.4);
	}
</style>
