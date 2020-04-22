<template>
    <div style="display: flex;">
        {{password}}
    </div>
</template>

<script>
export default {
    name: 'Back',
    data() {
        return {
            releaseJsonUrl: "https://raw.githubusercontent.com/Moxxel/CookAndConnect/dev/apk/release.json"
        };
    },
    computed: {
        password () {
        return this.$store.state.password
        }
    },
    methods: {
        getReleaseJson: function () {
            // Requête ajax pour récuprer le json
            
        }
    }
};
</script>

<style>

</style>