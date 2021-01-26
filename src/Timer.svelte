<script>
    import { createEventDispatcher } from 'svelte';
    import Progress from './Progress.svelte';

    const totalSeconds = 5;
    let secondsLeft = totalSeconds;
    let isRunning = false;
    $: progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100
    const dispatch = createEventDispatcher();

    function startTimer() {
        isRunning = true;
        let timer = setInterval(() => {
        secondsLeft -= 1;
            if(secondsLeft == 0) {
                clearInterval(timer);
                isRunning = false;
                secondsLeft = totalSeconds;
                dispatch('endTimer');
            }
        }, 1000);
    }

</script>
<style>
    h2 {
        margin: 0;
    }
    .start {
        background-color: rgb(154, 72, 76);
        width: 100%;
        margin: 10px 0;
    }
    .start[disabled] {
        background-color: #e3e3e3;
        cursor: not-allowed;
    }
</style>
<div bp="grid">
    <h2 bp="offset-5@md 4@md 12@sm">Seconds left: {secondsLeft}</h2>
</div>

<Progress progress={progress} />

<div bp="grid">
    <button disabled={isRunning} on:click={startTimer} bp="offset-5@md 4@md 12@sm" class="start">Start</button>
</div>
