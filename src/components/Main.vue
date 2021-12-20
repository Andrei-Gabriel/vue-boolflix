<template>
    <main>
        <div class="main-content">
            <div class="card" 
                 v-for="(elem, index) in 10" 
                 :key="index"
                 @mouseover="MouseHover(mouseHover)" 
                 @mouseleave="MouseNotHover(mouseHover)">

                <div class="card-content-true" v-if="mouseHover">
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
                        <span v-for="(elem, index) in stars[index]" :key="index"><i class="fas fa-star"></i></span>
                        <!--  / PROVVISORIO -->
                    </div>
                    <div>
                        <span class="Descrizione">Descrizione: </span>
                        <span>Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit quisquam quae soluta consectetur ex beatae ea nam porro laborum cupiditate, cumque vitae alias excepturi libero? A eveniet necessitatibus quo odio!</span>
                    </div>
                </div>

                <div class="card-content-false" v-else>
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

        data() {
            let mouseHover = false;
            // PROVVISORIO
            let stars = [];
            for(let i = 0; i < 10; i++){
                stars[i] = (Math.floor(Math.random() * 5) + 1);
            }
            //  / PROVVISORIO
            return {
                mouseHover,
                // PROVVISORIO
                stars,
                //  / PROVVISORIO
            }
        },
        methods: {
            MouseHover() {
                this.mouseHover = true;
            },
            MouseNotHover() {
                this.mouseHover = false;
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
            width: calc(100% / 4 - 40px);
            min-height: $cardHeight;
            max-height: $cardHeight;
            overflow-y: auto;
            border: 2px solid #b5b5b5;     
            margin: 30px 20px;
            .card-content-true {
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
                            color: #ffbd00;
                        }
                    }
                }
            }
            .card-content-false {
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