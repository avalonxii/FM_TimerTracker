
<script>

	import Card from '$lib/card.svelte'
	import UserCard from '$lib/cardUser.svelte'
	import {user} from '../data/data.js'


	

</script>

<div class="container">
	<UserCard photo={user.photo} name={user.name}/>
	
		<div class="container__cards">
			{#each user.info as {title, timeframes, icon, color}}
				<Card title={title} timeframes={timeframes} icon={icon} color={color}/>
			{/each}
		</div>
</div>

<style lang="scss">

	:global(body){
		background-color: $neutral-Very-dark-blue;
		min-height: 100vh;

		display: flex;
		justify-content: center;
		align-items: center;

		font-family: 'Rubik', sans-serif;
    	font-weight: 300;
	}

	.container{
		display: flex;
		flex-direction: column;
		gap: 1.4rem;

		padding: 5rem 0 5rem 0;

		@include desktop{
			flex-direction: row;
		}
	}

	.container__cards{
		display: flex;
		flex-direction: column;
		gap: 1.4rem;

		@include desktop{
			display: grid;
			grid-template-columns: 1fr 1fr 1fr;
		}
	}
	
</style>

