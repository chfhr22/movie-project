<template>
    <div class="header__intro">
        <div class="img">
            <img :src="'https://image.tmdb.org/t/p/w500' + movieBasic.poster_path" alt="">
        </div>
        <div class="header__info">
            <div class="info__wrap">
                <div class="title" v-if="movieBasic">{{movieBasic.title}}</div>
                <div class="desc">{{movieBasic.overview}}</div>
                <div class="grade">⭐{{movieBasic.vote_average}}</div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    props: {
        movieBasic: {
            type: Object,
            required: true,
        },
    },
    mounted() {
        console.log('movieBasic received:', this.movieBasic);
    }
}
</script>