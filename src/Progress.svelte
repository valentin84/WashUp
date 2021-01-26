<script>
    export let progress = 0;
</script>
<style>
    .progress-container {
        margin: 20px 0;
        border: solid #867e7e 1px;
    }

    .progress-bar {
        height: 30px;
        background-color: green;
    }


</style>

<div bp="grid">
    <div bp="offset-5@md 4@md 12@sm" class="progress-container">
        <div class="progress-bar" style="width: {progress}%">
            <span class="sr-only">
                { progress }
            </span>
        </div>
    </div>
</div>