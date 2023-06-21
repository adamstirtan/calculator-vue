<script setup>
    import { buttons } from '../buttons'

    const handleButtonClick = function(button) {
        console.log(button)
    }
</script>

<template>
    <div class="container">
        <div class="display">
            <div class="brand">
                <a href="https://github.com/adamstirtan/calcyoulator" target="_blank">
                    🔗 Adam Stirtan
                </a>
            </div>
            <div class="glass">
                1337
            </div>
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
    @import url('https://fonts.googleapis.com/css2?family=Martian+Mono&display=swap');

    .container {
        width: 500px;
        border: 3px solid #000;
        border-radius: 8px
    }

    .display {
        background-color: #212121;
        text-align: left;
        padding: 1rem 1rem 1.5rem 1rem;
        vertical-align: center;
    }

    .brand,
    .brand a {
        color: #fff;
        text-transform: uppercase;
        padding-bottom: 0.5rem;
    }

    .glass {
        background: #fff;
        border-radius: 10px;
        border: 1px solid rgba(255, 255, 255, 0.3);
        font-size: 3em;
        padding: 1rem;
        text-align: right;
        font-family: 'Martian Mono', monospace;
        color: #000;
    }

    .buttons {
        display: grid;
        background-color: #ededed;
        grid-template-columns: repeat(4, 1fr);
        grid-gap: 1rem;
        padding: 1rem;
        border-bottom-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }

    button {
        height: 80px;
        border: none;
        border-radius: 30px;
        font-size: 2em;
        background-color: #bdbdbd;
    }

    button:hover {
        box-shadow: inset 0 0 100px rgb(255, 255, 255, 0.3);
    }

    button.empty {
        visibility: hidden;
    }

    button.clear {
        color: #fff;
        background-color: #F44336;
    }

    button.func,
    button.operator {
        color: #fff;
        background-color: #757575;
    }

    button.calculate {
        color: #fff;
        background-color: #4CAF50;
    }
</style>