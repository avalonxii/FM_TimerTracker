<script>
	import Motion from 'svelte-motion/src/motion/MotionSSR.svelte'
	import {cardHover} from './animations/animation'
	import icon_options from '../images/icon-ellipsis.svg';
	import {timeframe} from './store.js'

	// component's props
	export let title
	export let timeframes
	export let icon
	export let color
	
</script>

<div class="card" style="--theme-color: {color}">

	<img class="card__icon" src={icon} alt="nose">

	<Motion whileHover={cardHover} let:motion>
		<div class="card__info" use:motion>
			<div class="card__top">
				<span class="card__title">{title}</span>
				<span class="card__options"><img src={icon_options} alt={icon_options} /></span>
			</div>
			<div class="card__bottom">
				
				{#if $timeframe === 'Daily'}
				<span class="card__current">{timeframes.daily.current}hrs</span>
				<div class="card__previous">Last Week - {timeframes.daily.previous}hrs</div>
				{:else if $timeframe === 'Weekly'}
				<span class="card__current">{timeframes.weekly.current}hrs</span>
				<div class="card__previous">Last Week - {timeframes.weekly.previous}hrs</div>
				{:else}
				<span class="card__current">{timeframes.monthly.current}hrs</span>
				<div class="card__previous">Last Week - {timeframes.monthly.previous}hrs</div>
				{/if}
				
			</div>
		</div>
	</Motion>
</div>

<style lang="scss">

	.card{
		background-color: var(--theme-color);
		position: relative;
		
		width: 100%;

		border-radius: $radius;
		color: white;
		overflow: hidden;

		display: flex;

		@include desktop {
			width: 250px;
		}

		.card__icon{
			position: absolute;
			z-index: 0;
			right: 1.6rem;
			top: -0.3rem;
		}

		.card__info{
			background-color: $neutral-Dark-blue;
			width: 100%;
			height: 80%;
			margin-top: 3.1rem;

			padding: $padding;
			border-top-left-radius: $radius;
			border-top-right-radius: $radius;
			z-index: 1;

			align-self: flex-end;

			.card__top{
				display: flex;
				justify-content: space-between;

				font-size: 18px;
				font-weight: 500;

				.card__title{
					font-weight: 300;
				}

				.card__options{
					cursor: pointer;
				}

			}

			.card__bottom{
				display: flex;
				justify-content: space-between;
				margin-top: 0.5rem;

				display: flex;
				align-items: center;

				@include desktop{
					flex-direction: column;
					align-items: start;

					margin-top: 1rem;
					gap: 0.4rem;

				}

				.card__current{
					font-size: 2rem;
					font-weight: 400;

					@include desktop{
						font-size: 3rem;
					}
				}

				.card__previous{
					font-size: 0.9rem;
					color: $neutral-Pale-blue
				}
			}
		}
	}
</style>
