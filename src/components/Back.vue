<template>
    <div style="display: flex;">
        {{password}}
    </div>
</template>

<script>
export default {
    name: 'Back',
    computed: {
        password () {
        return this.$store.state.password
        }
    },
    methods: {
        getReleaseJson: function () {
            
        }
    }
};
</script>

<style>

</style>