<template>
    <div>
        <div class="stape container">
            <h3>Les étapes de téléchargement</h3>
            <ul>
                <li>Téléchargez l'application en cliquant sur le bouton</li>
                <li>Connectez-vous sur votre tablette et rendez-vous sur la même page</li>
                <li>Téléchargez l'appli</li>
            </ul>
            <router-link to="/en-savoir-plus"><a href="#">En savoir plus..</a></router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Documentation',
    data () {
        return {

        }
    }
}
</script>

<style scoped lang="less">
.stape {
    margin-top: 1rem;
    > h3 {
        font-size: 28px;
        font-weight: normal;
    }
    > ul {
        text-align: center;
        list-style: none;
        > li {
            font-size: 18px;
        }
    }
}
</style>
