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
        onInput(event) {
            this.$emit('termChange', event.target.value);
        }
    }
});
</script>