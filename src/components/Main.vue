<template>
    <main>
        <div class="main-content">
            <div class="card-list">
                <Cards :film="film"
                    v-for="(film, index) in film" :key="index"
                />
            </div>
        </div>

        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" integrity="sha512-1ycn6IcaQQ40/MKBW2W4Rhis/DbILU74C1vSrLJxCq57o941Ym01SwNsOMqvEBFlcgUa6xLiPY/NS5R+E6ztJQ==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    </main>
</template>

<script>
    import Cards from './elements/Cards.vue';

    export default {
        name: 'Main',
        components: {
            Cards,
        },
        props: {
            film: Array,
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
            .card-list {
                display: flex;
                flex-wrap: wrap;
            }
        }
    }
</style>