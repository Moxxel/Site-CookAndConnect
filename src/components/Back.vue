<template>
    <div role="tablist">
        <b-card v-for="(release, index) in releases" :key="index" no-body class="mb-1">
            <b-card-header header-tag="header" class="p-1" role="tab">
                <b-button block href="#" v-b-toggle="'accordion-'+index" variant="info" style="background-color:#c4ad99; border-color:#c4ad99;display:flex; justify-content:space-between;"><span>{{ release.title }}</span> <span>V{{ release.version }}</span></b-button>
            </b-card-header>
            <b-collapse :id="'accordion-'+index" accordion="my-accordion" role="tabpanel">
                <b-card-body>
                    <b-card-text >
                        <p>{{ release.patch_notes }}</p>
                        <a :href="release.download_link"><i type="button" class="icon-cloud-download" style="font-size: 28px;"></i></a>
                    </b-card-text>
                </b-card-body>
            </b-collapse>
        </b-card>
    </div>
</template>

<script>
export default {
    name: 'Back',
    data() {
        return {
            releaseJsonUrl: "https://raw.githubusercontent.com/Moxxel/CookAndConnect/dev/apk/release.json",
            releases: []
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
            $.ajax({
                url: this.releaseJsonUrl,
                method: 'GET'
            }).done((response) => {
                this.releases = JSON.parse(response).releases;
            })
        }
    },
    mounted () {
        this.getReleaseJson()
    }
};
</script>

<style scoped lang="less">
.card-header {
    padding: 0;
    border-bottom: none;
}
.version-link {
    width: 100%;
    margin: 0;
    padding: 1rem;
    text-align: left;
    color: #c4ad99;
    transition: all 0.5s ease;
    text-decoration: none;
    display: flex;
    justify-content: space-between;
}
.version-link:hover {
    background-color: rgba(#c4ad99, 0.5);
    color: #fff;
    transition: all 0.5s ease;
}
.icon-cloud-download {
    background-color: transparent;
    font-size: 28px;
}
.icon-cloud-download:hover {
    text-decoration: none;
}
.card-body {
    display: flex;
    justify-content: space-between ;
    align-items: center;
    > p {
        margin-bottom: 0;
        font-size: 16px;
        text-align: left;
        display:flex; 
        justify-content: space-between; 
        width:100%;
    }
}
.card {
    border:none;
    background-color: transparent;
}
</style>