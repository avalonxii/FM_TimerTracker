
<script>
    import Motion from 'svelte-motion/src/motion/MotionSSR.svelte'
    import {linkSelected} from './animations/animation'
    import {buttonHover} from './animations/animation'
    import {buttonTap} from './animations/animation'
    import {timeframe} from './store.js'

    export let text

    function changeTimeframe() {
		timeframe.update( t => t = text);
	}

</script>


<Motion whileHover={buttonHover} whileTap={buttonTap} animate={ $timeframe === text? linkSelected: ''} let:motion>
    <button on:click={changeTimeframe} use:motion>{text}</button>
</Motion>


<style lang="scss">

    button{
        background: #ffffff00;
        border: none;
        font-size: 1.2rem;

        color: $neutral-Pale-blue;
        padding: 0.2rem 0.2rem 0.2rem 0;

        font-family: 'Rubik', sans-serif;
    	font-weight: 300;

        
    }

</style>