<template>
        <span class="films">
            {{filmTitle.title}}<br>
        </span>
</template>

<script>
    export default {
        name: 'Film',
        props: {
            film: {},
            human: {},
        },
        data() {
            return {
                films: {},
                filmTitle: {}
                // filmTitle: this.getFilm(),
            }
        },
        mounted() {
            fetch(this.film)
                .then(res => res.json())
                .then(data => this.filmTitle = data)
                .catch(err => console.log(err.message));
        }
    }
</script>

<style scoped>
    .films {
        display: flex;
        flex-direction: column;
        float: left;
        margin-left: 50px;
    }
</style>
