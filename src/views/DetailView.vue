<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <h1><a href="/">Mega Movie</a></h1>
            <nav>
                <ul>
                    <li><a href="/">넷플릭스</a></li>
                    <li><a href="/">디즈니</a></li>
                    <li><a href="/">애플TV</a></li>
                </ul>
            </nav>
        </div>
    </header>
    <main class="main">
        <DetailIntro v-if="movieBasic && movieInfo && movieCredits" :movieBasic="movieBasic" :movieInfo="movieInfo" :movieCredits="movieCredits"/>
        <!-- <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" /> -->
        <!-- <DetailReview v-if="movieReview" :movieReview="movieReview" /> -->
        <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" />
    </main>
</template>

<script>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axios from 'axios';

import DetailIntro from "../components/detail/DetailIntro.vue";
import DetailInfo from "../components/detail/DetailInfo.vue";
// import DetailReview from "../components/detail/DetailReview.vue";
import DetailCredits from "../components/detail/DetailCredits.vue";

export default {
    name: "MovieDetailPage",

    components: {
        DetailIntro,
        DetailInfo,
        // DetailReview,
        DetailCredits,
    },

    setup() {
        const movieBasic = ref(null);
        const movieInfo = ref(null);
        // const movieReview = ref(null);
        const movieCredits = ref(null);

        const route = useRoute();

        onMounted(async () => {
            const movieId = route.params.movieId;
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR";

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieBasic.value = resMovieBasic.data;
                console.log(resMovieBasic.data);

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieInfo.value = resMovieInfo.data;
                console.log(resMovieInfo.data);


                // const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/reviews?language=${language}&api_key=${apiKey}`);
                // movieReview.value = resMovieReview.data;
                // console.log(resMovieReview.data)


                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`);
                movieCredits.value = resMovieCredits.data;
                console.log(resMovieCredits.data)


            } catch (err) {
                console.log(err)
            }
        });

        return { movieBasic, movieInfo, movieCredits }
    }
}
</script>

<style lang="scss">
.header__inner {
    .header__nav {
        display: flex;
        justify-content: space-between;
        align-items: center;

        h1 {
            font-size: 25px;
            font-family: 'LotteriaDdag';
            padding: 3px 1rem;
            margin: 20px 10px;
            display: inline-block;
            text-transform: uppercase;
            color: #ffffff;
            font-weight: 900;
            border: 1px solid #fff;
            position: relative;

            span {
                font-size: 12px;
                align-content: center;
                justify-content: center;
                position: absolute;
                right: 5px;
                top: 0;
                color: #be0000;

            }
        }

        nav {
            li {
                display: inline;

                a {
                    font-weight: 700;
                    display: inline-block;
                    padding: 20px;
                }

                a:hover {
                    color: #ff0000;
                }
            }
        }
    }

}

.header__intro {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 30px;

    &::before {
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #00000032;
        // backdrop-filter: blur(5px);
        z-index: 1;
    }

    .container {
        display: flex;
        justify-content: space-between;
        position: relative;
        z-index: 10;

        .left {
            width: 350px;
        }

        .right {
            width: calc(100% - 390px);

            h2 {
                font-size: 30px;
                margin-bottom: 10px;
            }

            .desc {
                margin-bottom: 10px;
            }

            .credits {
                margin-top: 40px;
                width: 800px;
                display: flex;
                flex-direction: row;

                img {
                    padding: 10px;
                }
            }
        }
    }
}

.credit {
    width: 150px;
}
.credit div img {
    display: flex;
}
</style>