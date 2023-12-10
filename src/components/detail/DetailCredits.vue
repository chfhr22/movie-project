<template>
    <div class="movie__credits">
        <div class="credits__inner container">
            <h2>배우</h2>
            <div class="credit">
                <div v-for="(cast, index) in movieCredits.cast.slice(0, 4)" :key="index">
                    <img :src="'https://image.tmdb.org/t/p/w500' + cast.profile_path" :alt="cast.name">
                    <p>{{ cast.character }}</p>
                    <p>{{ cast.name }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        movieCredits: {
            type: Object,
            required: true,
        },
    },
    mounted() {
        console.log('movieBasic received:', this.movieCredits);
    }
}
</script>

<style lang="scss">
.movie__credits {
    padding: 2vh 0;

    .credits__inner {
        h2 {
            font-size: 2rem;
        }

        .credit {
            width: 100%;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;

            div {
                width: 23%;
                margin-bottom: 1vh;
                text-align: center;
                color: var(--white);
                font-size: 1rem;

                img {
                    width: 100%;
                    vertical-align: top;
                }
            }
        }
    }
}
</style>