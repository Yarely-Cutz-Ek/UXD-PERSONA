<script>

export default {
    
    data() {
        return {
            dato: '',
        }
    },
    methods: {
        enviar() {
            
            this.$emit('info',this.dato)
        }
    }
}
</script>

<template>
    <div class="">
        <input type="text" v-model="dato" name="info" id="info" class="w-full rounded-lg border-gray-200 p-3 text-sm"  @input="enviar">

    </div>
</template>