<script>

export default {
    
    data() {
        return {
            dato: '',
        }
    },
    methods: {
        enviar() {
            
            this.$emit('dato',this.dato)
        }
    }
}
</script>

<template>
        <textarea type="text" v-model="dato" name="dato" id="dato" class="w-full rounded-lg border-gray-200 p-3 text-sm"  rows="2" @input="enviar"></textarea>    

</template>