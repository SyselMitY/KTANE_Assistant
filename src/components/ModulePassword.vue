<template>
    <div class="module">

        <h2>Password</h2>

        <div class="bomb_input">
            <label for="row1">Row 1 </label>
            <input type="text" id="row1" v-model="row1"/>
        </div>

        <div class="bomb_input">
            <label for="row2">Row 2 </label>
            <input type="text" id="row2" v-model="row2"/>
        </div>
        <div class="bomb_input">
            <label for="row3">Row 3 </label>
            <input type="text" id="row3" v-model="row3"/>
        </div>
        <span>{{this.password}}</span>
    </div>
</template>

<script>
    export default {
        name: "ModulePassword",
        data() {
            return {
                row1: "",
                row2: "",
                row3: "",
                dictionary: [
                    "angst",
                    "atmen",
                    "beten",
                    "bombe",
                    "danke",
                    "draht",
                    "druck",
                    "drück",
                    "farbe",
                    "fehlt",
                    "ferse",
                    "kabel",
                    "knall",
                    "knapp",
                    "knopf",
                    "leere",
                    "legal",
                    "lehre",
                    "mathe",
                    "matte",
                    "panik",
                    "pieps",
                    "rauch",
                    "ruhig",
                    "saite",
                    "sehne",
                    "seite",
                    "sende",
                    "strom",
                    "super",
                    "timer",
                    "übrig",
                    "verse",
                    "warte",
                    "zange"
                ]
            }
        },
        computed: {
            password() {
                if (this.row1 === ""
                    || this.row2 === ""
                    || this.row3 === "") {
                    return "???";
                }
                return this.dictionary.filter(value => {
                    return this.row1.toLowerCase().includes(value.charAt(0).toLowerCase()) &&
                    this.row2.toLowerCase().includes(value.charAt(1).toLowerCase()) &&
                    this.row3.toLowerCase().includes(value.charAt(2).toLowerCase())
                }).join(", ");
            }
        }
    }
</script>

<style scoped>

</style>