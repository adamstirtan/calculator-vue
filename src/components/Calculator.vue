<script setup>
    import { computed, reactive } from 'vue'
    import { buttons } from '../buttons'

    const state = reactive({
        operation: [],
        formula: [],
        current: 0
    })

    const operationDisplay = computed(() => {
        return state.operation.join('')
    })

    const handleButtonClick = function(event) {
        const targetButton = event.target;
        buttons.forEach(button => {
            if (button.name == targetButton.id) {
                calculator(button)
            }
        })
    }

    const calculator = function(button) {
        switch (button.class) {
            case 'clear':
                state.operation = []
                break
            case 'number':
            case 'operator':
            case 'func':
                state.operation.push(button.label)
                state.formula.push(button.formula)
                break
            case 'calculate':
                calculate()
        }
    }

    const calculate = function() {
        state.current = 42
        console.log(`formula: {state.formula}`)
    }
</script>

<template>
    <div class="container">
        <div class="display">
            <div class="brand">
                <a href="https://github.com/adamstirtan/calcyoulator" target="_blank">
                    Adam Stirtan
                </a>
            </div>
            <div class="glass" >
                <div class="operation">
                    {{ operationDisplay }}
                </div>
                <div class="current">
                    {{ state.current }}
                </div>
            </div>
        </div>
        <div class="buttons">
            <button
                v-for="button in buttons"
                :key="button.name"
                :id="button.name"
                :value="button.formula"
                :class="button.class"
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
        padding: 1rem 1rem 1.5rem 1rem;
        vertical-align: center;
    }

    .brand,
    .brand a {
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        color: #fff;
        text-align: left;
        text-transform: uppercase;
        padding-bottom: 0.5rem;
        font-size: 0.9em;
        text-decoration: none;
    }

    .glass {
        background: #fff;
        border-radius: 10px;
        padding: 1rem;
        text-align: right;
        font-family: 'Martian Mono', monospace;
        color: #000;
    }

    .operation {
        min-height: 22px;
        font-size: 1.1em;
    }

    .current {
        font-size: 3em;
    }

    .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        grid-gap: 1rem;
        padding: 1rem;
        background-color: #fff;
    }

    button {
        height: 64px;
        border: none;
        border-radius: 16px;
        font-size: 2em;
        background-color: #bdbdbd;
    }

    button:hover {
        cursor: pointer;
        box-shadow: inset 0 0 100px rgb(255, 255, 255, 0.3);
    }

    button.empty {
        visibility: hidden;
    }

    button.key {
        color: #fff;
        background-color: #536DFE;
    }

    button.operator,
    button.func {
        color: #fff;
        background-color: #757575;
    }

    button.clear {
        color: #fff;
        background-color: #F44336;
    }

    button.calculate {
        color: #fff;
        background-color: #4CAF50;
    }
</style>