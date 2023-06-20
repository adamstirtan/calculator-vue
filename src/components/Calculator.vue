<script setup>
    import { buttons } from '../buttons'

    //const buttons = ref(buttons);

    buttons.forEach(button => {
        console.log(button.label)
    })
</script>

<template>
    <div class="container">
        <div class="display">
            Display
        </div>
        <div class="buttons">
            <button
                v-for="button in buttons"
                :key="button.label"
                :value="button.value"
                :class="button.type"
                @click="handleButtonClick">
                {{ button.label }}
            </button>
        </div>
    </div>
</template>

<style scoped>
    .container {
        width: 500px;
        height: 600px;
        border: 3px solid #000;
        border-radius: 8px
    }

    .display {
        height: 120px;
        background-color: hsl(0, 0%, 0%);
        color: #fff;
        text-align: right;
    }

    .buttons {
        display: grid;
        background-color: #ededed;
        grid-template-columns: repeat(4, 1fr);
        grid-gap: 1rem;
        padding: 1rem
    }

    button {
        height: 100px;
        border: none;
        border-radius: 40px;
        font-size: 2em;
    }

    button.empty {
        visibility: hidden;
    }

    button.clear {
        color: #fff;
        background-color: red;
    }
</style>