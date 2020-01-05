<template>
    <div class="module">
        <h2>Cable Sequence</h2>
        <div class="colors">
            <span class="sequence-input" id="red" @click="currentColor='red'"/>
            <span class="sequence-input" id="blue" @click="currentColor='blue'"/>
            <span class="sequence-input" id="black" @click="currentColor='black'"/>
        </div>
        <div class="connections">
            <span class="sequence-input" @click="setOutput('A')">A</span>
            <span class="sequence-input" @click="setOutput('B')">B</span>
            <span class="sequence-input" @click="setOutput('C')">C</span>
        </div>
        <span id="result">{{this.cutTheWire}}</span>
    </div>
</template>

<script>
    export default {
        name: "ModuleCableSequence",
        data() {
            return {
                currentColor: "",
                cutTheWire: "",
                counterRed: 0,
                counterBlue: 0,
                counterBlack: 0,
                redLogic: ["C", "B", "A", "AC", "B", "AC", "ABC", "AB", "B"],
                blueLogic: ["B", "AC", "B", "A", "B", "BC", "C", "AC", "A"],
                blackLogic: ["ABC", "AC", "B", "AC", "B", "BC", "AB", "C", "C"]
            }
        },
        methods: {
            setOutput(wire) {
                if (this.calculateCutting(wire)) this.cutTheWire = "Durchschneiden";
                else this.cutTheWire = "Nicht Durchschneiden";
            },
            calculateCutting(wire) {
                switch (this.currentColor) {
                    case "red":
                        return this.redLogic[this.counterRed++].includes(wire);
                    case "blue":
                        return this.blueLogic[this.counterBlue++].includes(wire);
                    case "black":
                        return this.blackLogic[this.counterBlack++].includes(wire);
                }
            }
        }
    }
</script>

<style scoped>
    .sequence-input {
        width: 1em;
        height: 1em;
        padding: 0.5em;
        margin: 0.5em;
        border: 2px solid black;
        display: inline-block;
    }

    #red {
        background-color: red;
    }

    #blue {
        background-color: blue;
    }

    #black {
        background-color: black;
    }
</style>