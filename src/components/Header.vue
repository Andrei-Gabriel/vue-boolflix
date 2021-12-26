<template>
    <header>
        <div class="header-content">
            <h1>NETFLIX</h1>
            <form @submit.prevent="$emit('ricerca', inputQuery)">
                <input type="text" placeholder="Cerca qualcosa da guardare" v-model="inputQuery">
                <button class="search-btn">Cerca</button>
            </form>
        </div>
    </header>
</template>

<script>
    export default {
        name: 'Header',
        data() {
            return {
                inputQuery: "",
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../assets/style/variables.scss';

    header {
        background-color: #000;
        .header-content {
            max-width: $widthContent;
            margin: $marginConten;
            height: 120px;
            padding: 0 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            // Stile componenti di .header-content
            h1 {
                color: #e50914;
                font-size: 50px;
            }
            input, .search-btn {
                line-height: 2;
                border: none;
                border-radius: 7px;
                padding: 0 15px;
            }
            input {
                width: 250px;
                background-color: #303030;
                color: white;
            }
            input:hover {
                opacity: 0.8;
            }
            .search-btn {
                background-color: #e50914;
                color: #fff;
                cursor: pointer;
                margin-left: 7px;
            }
            .search-btn:hover {
                opacity: 0.7;
            }
        }
    }
</style>