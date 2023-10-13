<template>
    <p>{{ message }}</p>
</template>
<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import axios from 'axios';

export default defineComponent({
    setup(){
        const message = ref ('');

        const paises =async () => {
            try {
                const response = await axios.get(`api/v1/country`);
                message.value = response.data;
                console.log(message.value);
            } catch (error) {
                console.error("Hubo un error: ", error.message);
            } 
        }

        onMounted(() => {
            paises();
        });

        return {
            message
        };


    }
});
</script>