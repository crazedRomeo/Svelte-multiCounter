<script lang="ts">
    export let value;
    export let increment;
    export let decrement;
    export let refresh;
    export let cancel;
    export let changeTitle;
    export let inputElement;

    function changeTitle1(event) {
        value.title = event.target.value;
        changeTitle(event);
    }
    
</script>   

<div class="counter">
    <input type="text" class="counter-name" value={value.title} id={value.id} on:input={changeTitle1} bind:this={inputElement}/>
    <span class="counter-value">
        {value.value}
    </span>
    <div class="counter-controls">
        <button class="btn btn-plus" on:click={increment(value.id)}>+</button>
        <button class="btn btn-minus" on:click={decrement(value.id)}>-</button>
        <button class="btn btn-zero" on:click={refresh(value.id)}>0</button>
        <span class="btn-cancel" on:click={cancel(value.id)}>x</span>
    </div>
</div>

<style lang="scss">
.counter {
    background-color: rgb(247,250,252);
    border-radius: 0.25rem;
    display: flex;
    align-items: center;
    position: relative;
    max-width: 24rem;
    margin: auto;
    margin-bottom: 0.5rem;
    box-shadow: 0 10px 15px -3px rgba(0,0,0,.1), 0 4px 6px -2px rgba(0,0,0,.05);
}

.counter .counter-name {
    margin: 0 1rem;
    padding: 0 0.25rem;
    color: rgb(113,128,150);
    width: 8rem;
    border: 0;
}

.counter .counter-value {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    font-weight: 700;
    font-size: 1.125rem;
    padding: 0 1rem;
}

.counter .counter-controls {
    margin-left: auto;
    display: flex;
}

.counter .btn {
    color: #fff;
    padding-top: 0.25rem;
    padding-bottom: 0.25rem;
    padding-left: 0.75rem;
    padding-right: 0.75rem;
    margin-top: 0.25rem;
    margin-bottom: 0.25rem;
    font-size: 1.125rem;
    line-height: inherit;
    cursor: pointer;
}

.counter .btn.btn-plus {
    background-color: rgb(245,101,101);
    border-top-left-radius: 0.25rem;
    border-bottom-left-radius: 0.25rem;
    border: 0;
}

.counter .btn.btn-minus {
    background-color: rgb(66,153,225);
    border: 0;
}

.counter .btn.btn-zero {
    background-color: rgb(236,201,75);
    border-top-right-radius: 0.25rem;
    border-bottom-right-radius: 0.25rem;
    border: 0;
}

.counter .btn-cancel {
    padding: 0.5rem 1rem;
    cursor: pointer;
    color: rgb(160,174,192);
}
</style>
