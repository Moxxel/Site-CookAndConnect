<template>
    <div>
        <div v-for="(release, index) in releases" :key="index" class="card">
            <div class="card-header" :id="'ab'+index">
                <h5 class="mb-0">
                    <a class="btn btn-link collapsed version-link" type="button" data-toggle="collapse" :data-target="'#'+'a'+index" aria-expanded="false" :aria-controls="'a'+index">
                        Version 1.1
                    </a>
                </h5>
            </div>
            <div :id="'a'+index" class="collapse" :aria-labelledby="'a'+index" :data-parent="'#'+'ab'+index">
                <div class="card-body">
                    <p>Création d'un utilisateur Cuisinier</p>
                    <i type="button" href="#" class="icon-cloud-download" style="font-size: 28px;"></i>
                </div>
            </div>
        </div>
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
                console.log(this.releases)
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
}
.version-link {
    width: 100%;
    margin: 0;
    padding: 1rem;
    text-align: left;
    color: #c4ad99;
    transition: all 0.5s ease;
    text-decoration: none;
}
.version-link:hover {
    background-color: rgba(#c4ad99, 0.5);
    color: #fff;
    transition: all 0.5s ease;
}
.card-body {
    display: flex;
    justify-content: space-between ;
    align-items: center;
    > p {
        margin-bottom: 0;
        font-size: 16px;
        margin-right: 3rem;
        text-align: left;
    }
}
</style>