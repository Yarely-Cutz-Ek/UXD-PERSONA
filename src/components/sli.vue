<script>

export default {

    data() {
        return {
            slider: 50
        }
    },
    methods: {
        enviar() {
            this.$emit('person', this.slider)
        }
    }
}
</script>

<template>
    <div class="flex">
        <h1 class="px-2">Extrovertido {{ this.slider }}% </h1>
        <input type="range" class="w-full py-2.5 px-5 rounded-lg bg-gray-100  focus:bg-white " id="person" placeholder=""
            typeof="slider" min="0" max="100" v-model="slider" @input="enviar">
        <h1> Introvertido {{ 100 - this.slider }}% </h1>
    </div>
</template>