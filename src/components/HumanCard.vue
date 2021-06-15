<template>
    <div class='human'>
        <div>
            <p>name: {{human.name}}</p>
            <p>height: {{human.height}} </p>
            <p>mass: {{human.mass}} </p>
            <p>hair color: {{human.hair_color}} </p>
            <p>skin color: {{human.skin_color}}</p>
            <div v-show="!btnIsClicked">
                <hr>
                <span class="more">
                    <strong>More Info</strong> 
                    <button class="btn" @click="clickMore"> V </button>
                </span>
            </div>
            <div v-show='btnIsClicked'>
                <span v-show="human.films.length">
                    <p>films: </p>
                    <Film
                        v-for="(film, i) in human.films" 
                        :key="film.i" 
                        :index=i
                        :film="film"
                        :human="human"
                    />
                </span>
                <span v-show="human.vehicles.length">
                    <p>vehicles: </p>
                    <Vehicle
                        v-for="(vehicle, i) in human.vehicles" 
                        :key="vehicle.i" 
                        :index=i
                        :vehicle='vehicle'
                        :human="human"
                    />
                </span>
                <span v-show="human.starships.length">
                    <p>starships: </p>
                    <Starship 
                        v-for="(starship, i) in human.starships" 
                        :key="starship.i" 
                        :index=i
                        :starship='starship'
                        :human="human"
                    />
                </span>
                <hr>
                <span class="more">
                    <strong>Less Info</strong> 
                    <button class="btnLess" @click="clickLess"> V </button>
                </span>
            </div>
        </div>
    </div>
</template>

<script>
    import Film from './Film'
    import Vehicle from './Vehicle'
    import Starship from './Starship'

    export default {
        name: 'HumanCard',
        components: {
            Film, Vehicle, Starship
        },
        props: {
            human: {},
        },
        data() {
            return {
                btnIsClicked: false,
            }
        },
        methods: {
            clickMore() {
                this.btnIsClicked = true;
            },
            clickLess() {
                this.btnIsClicked = false;
            },
        }
    }
</script>

<style scoped>
    .btn {
        font-size: 40px;
        margin: 10px 10px 10px 20px;
        border: solid 1px;
        border-radius: 50%;
    }
    .btnLess{
        font-size: 40px;
        margin: 10px 10px 10px 20px;
        transform: rotate(180deg);
        border: solid 1px;
        border-radius: 50%;
    }
    .more {
        align-items: center;
        display: flex;
        flex-direction: row;
    }
    span {
        display: flex;
        flex-direction: column;
    }
    .human {
        display: flex;
        float: left;
        padding-left: 5px;
        border: 1px solid;
        margin: 2px;
    }
    p {
        display: flex;
        justify-content: space-between;
    }
</style>