<template>
    <span v-if="human.vehicles.length">
        <span class="films">
            {{vehicleTitle.name}} <br>
        </span>
    </span>
</template>

<script>
    export default {
        name: 'Vehicle',
        props: {
            vehicle: {},
            human: {},
        },
        data() {
            return {
                vehicleTitle: {},
            }
        },
        mounted() {
            fetch(this.vehicle)
                .then(res => res.json())
                .then(data => this.vehicleTitle = data)
                .catch(err => console.log(err.message));
        }
    }
</script>

<style scoped>
    .films {
        display: flex;
        flex-direction: column;
        float: right;
        margin-left: 80px;
    }

</style>
