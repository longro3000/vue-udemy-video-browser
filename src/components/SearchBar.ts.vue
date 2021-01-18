<template>
    <div>
        <input @input='onInput'/>
    </div>
</template>
<script>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'SearchBar',
    methods: {
        onInput: (event) => {
            console.log(event.target.value);
        }
    }
});
</script>