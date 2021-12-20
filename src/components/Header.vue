<template>
    <header>
        <div class="header-content">
            <img src="../assets/img/logo_large.png" alt="">
            <form>
                <input type="text" placeholder="Cerca qualcosa da guardare">
            </form>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/variables.scss';

    header {
        background-color: #000;
        .header-content {
            width: $widthContent;
            height: 120px;
            margin: $marginConten;
            display: flex;
            align-items: center;
            justify-content: space-between;
            // Stile componenti di .header-content
            img {
                width: 175px;
            }
            input {
                line-height: 2;
                width: 250px;
                padding: 0 7px;
                border: none;
                border-radius: 7px;
                background-color: #303030;
                color: white;
            }
        }
    }
</style>