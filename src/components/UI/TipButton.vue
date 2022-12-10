<template>
    <button>
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name:"TipButton"
    }
</script>

<style lang="scss" scoped>
    button {
        width: 70px;
        height: 40px;

        font-size: 16px;
        
        border: none;
        border-radius: 10px;

        background-color: rgba(0, 128, 128, 0.493);

        cursor: pointer;

        margin: 15px;
    }
</style>