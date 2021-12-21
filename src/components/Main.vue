<template>
    <main>
        <div class="main-content">
            <div class="card" 
                 v-for="(elem, index) in 10" 
                 :key="index"
                >

                <div class="card-content">
                    <div>
                        <span class="titolo">Titolo: </span>
                        <span>Lorem, ipsum dolor.</span>
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
        </div>

        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" integrity="sha512-1ycn6IcaQQ40/MKBW2W4Rhis/DbILU74C1vSrLJxCq57o941Ym01SwNsOMqvEBFlcgUa6xLiPY/NS5R+E6ztJQ==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    </main>
</template>

<script>
    export default {
        name: 'Main',
        methods: {
            getFillStars(vote) {
                return Math.ceil(vote / 2); 
            }
            // isMouseHover() {
            //     if(this.mouseHover == false){
            //         this.mouseHover = true;
            //     } else {
            //         this.mouseHover = false;
            //     }
            // }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../assets/style/variables.scss';

    main {
        .main-content {
            max-width: $widthContent;
            margin: $marginConten;
            padding: 20px 0;
            display: flex;
            flex-wrap: wrap
        }
        // Stile .card
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
                    margin-top: 7px;
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
        // .card:hover {
        //     background-image: none;
        //     background-color: #000;
        // }
    }
</style>