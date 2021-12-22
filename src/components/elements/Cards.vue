<template>
    <div class="card">
        <div class="card-content">
            <div>
                <span class="titolo">Titolo: </span>
                <span>{{film.title}}</span>
            </div>
            <div>
                <span class="titolo-originale">Titolo originale: </span>
                <span>Lorem, ipsum dolor.</span>
            </div>
            <div>
                <span class="voto">Voto: </span>
                <!-- PROVVISORIO -->
                <span v-for="i in 5" :key="i">
                <i v-if="i <= getFillStars(6)" class="fas fa-star yellowStar"></i>
                <i v-else class="far fa-star"></i>
                </span>
                <!--  / PROVVISORIO -->
            </div>
            <div>
                <span class="Descrizione">Descrizione: </span>
                <span>Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit quisquam quae soluta consectetur ex beatae ea nam porro laborum cupiditate, cumque vitae alias excepturi libero? A eveniet necessitatibus quo odio!</span>
            </div>
            </div>

        <div class="card-image">
            <img src='https://picsum.photos/300/400'>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Cards',
        props: {
            films: Array,
        },
        methods: {
            getFillStars(vote) {
                return Math.ceil(vote / 2); 
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../../assets/style/variables.scss';
 
    .card {
        position: relative;
        width: calc(100% / 4 - 40px);
        min-height: $cardHeight;
        max-height: $cardHeight;
        overflow-y: auto;
        border: 2px solid #b5b5b5;     
        margin: 30px 20px;
        .card-content {
            opacity: 0;
            transition: 0.4s opacity;
            position: absolute;
            z-index: 1;
            width: 100%;
            height: 100%;
            background-color: #000;
            padding: 25px 10px;
            div {
                margin-top: 9px;
                span:first-child {
                font-weight: bold;
            }
                span {
                    color: #fff;
                    i {
                        color: #434343;
                    }
                    .yellowStar {
                        color: #ffbd00;
                    }
                }
            }
            &:hover {
                opacity: 1;
            }
        }
        .card-image {
            width: 100%;
            height: 100%;
            img {
                width: 100%;
                height: 100%;
                display: block;
            }
        }
    }
</style>