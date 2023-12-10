<template>
    <div class="header__intro">
        <div class="img">
            <img :src="'https://image.tmdb.org/t/p/w500' + movieBasic.poster_path" alt="">
        </div>
        <div class="container">
            <div class="info__wrap">
                <div class="title" v-if="movieBasic">{{movieBasic.title}}</div>
                <div class="desc">{{movieBasic.overview}}</div>
                <div class="grade">⭐{{movieBasic.vote_average}}</div>
                <div v-if="movieInfo && movieInfo.genres && movieInfo.genres.length && movieCredits">
                   <div>
                    <i>감독 : </i>
                    <span>
                        {{ movieCredits.crew[0].name }}
                    </span>
                   </div>
                    <div>
                        <i>장르 : </i>
                    <span v-for="(genre, index) in movieInfo.genres" :key="index">
                        {{ genre.name }}
                        <span v-if="index < movieInfo.genres.length - 1">, </span>
                    </span>
                    </div>
                </div>
                <div>
                    <i>개봉일 : </i>
                    <span>
                        {{ movieInfo.release_date }}
                    </span>
                </div>
                <div>
                    <i>상영시간 : </i>
                    <span>
                        {{ movieInfo.runtime }}
                    </span>
                    분
                </div>
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
        movieInfo: {
            type: Object,
            required: true
        },
        movieCredits: {
            type: Object,
            required: true
        }
    },
    mounted() {
        console.log('movieBasic received:', this.movieBasic);
    }
}
</script>

<style lang="scss">
i {
    display: inline-block;
    margin-top: 5px;
    margin-right: 5px;
}
.header__intro {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-40%, 0%);
    display: flex;
    // flex-wrap: wrap;
    align-items: center;
    justify-content: space-around;
    // height: 700px;
    // background-image: url(https://image.tmdb.org/t/p/w500/xgGGinKRL8xeRkaAR9RMbtyk60y.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;

    .img {
        // margin-left: 100px;
        // display: flex;
        // justify-content: center;
        // background-image: url(https://image.tmdb.org/t/p/w500/7M2pc9OboapgtoBbkU49Aim7O5B.jpg);
        // background-size: contain;
        // background-repeat: no-repeat;
        img {
            width: 80%;
            padding-left: 20vh;
            // height: 80%;
        }
    }

        .info__wrap {
            display: flex;
            // flex-wrap: wrap;
            flex-direction: column;
            background-color: #00000031;
            padding: 50px;
            
            .title {
            font-size: 2.5rem;
            font-weight: 600;
            color: var(--white);
            margin-bottom: 10px;

            @media(max-width: 1080px){
                font-size: 2rem;
            }
            }
            .desc {
                color: var(--white);
                overflow: hidden;
                text-overflow: ellipsis;
                display: -webkit-box;
                -webkit-line-clamp: 3; 
                -webkit-box-orient: vertical;
                width: 70%;
                margin-bottom: 10px;
            }
            .grade {
                color: var(--white);
                margin-bottom: 10px;
            }
        
    }
}
</style>