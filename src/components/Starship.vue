<template>
        <span class="films">
            {{starshipTitle.name}} <br>
        </span>
</template>

<script>
    export default {
        name: 'Film',
        props: {
            starship: {
                type: String,
                required: true,
            },
            human: {},
        },
        data() {
            return {
                starshipTitle: {},
            }
        },
        mounted() {
            fetch(this.starship)
                .then(res => res.json())
                .then(data => this.starshipTitle = data)
                .catch(err => console.log(err.message));
        }
    }
</script>

<style scoped>
    .films {
        display: flex;
        flex-direction: column;
        float: left;
        margin-left: 80px;
    }
</style>