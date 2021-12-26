<template>
    <div class="card">
        <div class="card-content">
            <div class="generali">
                <div>
                    <span class="titolo">Titolo: </span>
                    <span>{{serie.title}}</span>
                </div>
                <div>
                    <span class="titolo-originale">Titolo originale: </span>
                    <span>{{serie.original_title}}</span>
                </div>
                <div>
                    <span class="lingua">Lingua: </span>
                    <!-- Come gestire meglio le differenze tra MDBootstrap e l'API??? -->
                    <i v-if="serie.original_language == 'en'" class="flag flag-gb uk"></i>
                    <i v-else-if="serie.original_language == 'ja'" class="flag flag-jp"></i>
                    <!-- Questo forse non copre tutti i casi -->
                    <i v-else :class="`flag flag-${serie.original_language}`"></i>
                </div>
                <div>
                    <!-- <span v-if="!film.vote_average">*VOTO NON DISPONIBILE*</span> -->
                    <span v-if="serie.vote_average" class="voto">Voto: 
                        <span v-for="i in 5" :key="i">
                            <i v-if="i <= getFillStars(serie.vote_average)" class="fas fa-star yellowStar"></i>
                            <i v-else class="far fa-star"></i>
                        </span>
                    </span>
                </div>
            </div>
            <div class="descrizione" style="overflow-y: auto; height: calc(60% - 12px); margin-top: 12px">
                <span v-if="serie.overview">Descrizione: <span style="font-weight: normal">{{serie.overview}}</span></span>
                <span v-else style="display: inline-block; text-align: center;">*DESCRIZIONE NON DISPONIBILE*</span>
            </div>
        </div>

        <div class="card-image">
            <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`">
            <div v-else class="no-poster">
                <span>poster non disponibile</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CardSerie',
        props: {
            serie: Object,
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
    @import '~mdb-ui-kit/css/mdb.min.css';
    
    span {
        pointer-events: none;
    }
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
            .generali {
                overflow-y: auto;
                max-height: 40%;
                min-height: 40%;
            }
            .generali div:first-child{
                margin-top: 0;
            }
            .descizione > div, .generali > div {
                margin-top: 9px;
                
            }
            &:hover {
                opacity: 1;
            }
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
        .card-image {
            width: 100%;
            height: 100%;
            img {
                width: 100%;
                height: 100%;
                display: block;
            }
            .no-poster {
                background-color: black; 
                height: 100%; 
                width: 100%; 
                display: flex; 
                align-items: center; 
                justify-content: center; 
                color: white;
                span {
                    display: block;
                    text-align: center;
                    font-size: 25px;
                    text-transform: uppercase;
                }
            }
        }
    }
</style>