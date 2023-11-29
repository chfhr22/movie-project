<script setup>
    const {movies} = defineProps(['movies']);
</script>

<template>
    <header id="header" :movies="movies">
        <div class="contain">
            <!-- <img src="https://image.tmdb.org/t/p/xgGGinKRL8xeRkaAR9RMbtyk60y.jpg" alt=""> -->
            <div class="header__inner">
                <h1>Mega Movie</h1>
                <nav>
                    <ul>
                        <li><a href="/">넷플릭스</a></li>
                        <li><a href="/">디즈니</a></li>
                        <li><a href="/">애플TV</a></li>
                    </ul>
                </nav>
            </div>
            <div class="header__intro" >
                <!-- <img src="https://image.tmdb.org/t/p/w100%/xgGGinKRL8xeRkaAR9RMbtyk60y.jpg" alt=""> -->
                <div class="img">
                    <img src="https://image.tmdb.org/t/p/w500/7M2pc9OboapgtoBbkU49Aim7O5B.jpg" alt="">
                </div>
                <div class="header__info">
                    <div class="info__wrap">
                        <div class="title">Trolls Band Together</div>
                        <div class="desc">전 세계 모든 트롤을 열광케 했던 최고의 아이돌 그룹 ‘브로존’. 역대급 무대 실수와 형제 간의 불화로 결국 해체한 뒤, 모두에게 잊혀 간다. 그러던 어느 날, ‘브로존’의 황금막내 ‘브랜치’는 메인보컬 ‘플로이드’가 슈퍼스타 ‘벨벳’과 ‘비니어’에게 잡혀 재능을 빼앗기고 있다는 소식을 듣는다. 그를 구하기 위해서는 흩어져 있는 ‘브로존’을 재결합하고 완벽한 화음을 되찾아야 하는데… 12월, 가장 짜릿한 컴백 무대의 시작!</div>
                        <div class="grade">⭐7.2</div>
                        <div class="credit">
                            <div>
                                <img src="https://image.tmdb.org/t/p/w200/yirl6fEmeXY5xcvJw3nTcCNq9Cw.jpg" alt="">
                                <img src="https://image.tmdb.org/t/p/w200//6Yk5t9RwkdkAT8Qv45934Eez2CA.jpg" alt="">
                                <img src="https://image.tmdb.org/t/p/w200/8XJzD4mrxlBvtYjP1wVNTW5K9ya.jpg" alt="">
                                <img src="https://image.tmdb.org/t/p/w200/e9XlcFnZQiBSQ1vISQVyTOrkIaq.jpg" alt="">
                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </header>
</template>

<style lang="scss">
#header {
}
.header__inner {
    height: 70px;
    display: flex;
    justify-content: space-between;
    h1 {
        font-size: 1.5rem;
        font-weight: 600;
        color: var(--red);
        font-family: var(--mainfont-nexon);
        padding: 18px 1rem;
        text-transform: uppercase;
        
    }

    nav {
        ul {
            display: flex;
            li {
                margin-left: 10px;
                a {
                    color: var(--white);
                    padding: 10px 20px;
                    line-height: 70px;

                    &:hover {
                        color: var(--red);
                    }
                }
            }
        }
    }
}
.header__intro {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-around;
    height: 700px;
    background-image: url(https://image.tmdb.org/t/p/w500/xgGGinKRL8xeRkaAR9RMbtyk60y.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;

    .img {
        // margin-left: 100px;
        display: flex;
        justify-content: center;
        // background-image: url(https://image.tmdb.org/t/p/w500/7M2pc9OboapgtoBbkU49Aim7O5B.jpg);
        // background-size: contain;
        // background-repeat: no-repeat;
        img {
            width: 80%;
            height: 80%;
        }
    }
    .header__info {
        width: 50%;

        .info__wrap {
            display: flex;
            // flex-wrap: wrap;
            flex-direction: column;
            
            .title {
            font-size: 2.5rem;
            font-weight: 600;
            color: var(--white);
            margin-bottom: 10px;
            }
            .desc {
                color: var(--white);
                overflow: hidden;
                text-overflow: ellipsis;
                display: -webkit-box;
                -webkit-line-clamp: 3; 
                -webkit-box-orient: vertical;
                width: 80%;
                margin-bottom: 10px;
            }
            .grade {
                color: var(--white);
                margin-bottom: 10px;
            }
            .credit {
                width: 100%;
                div {
                    display: flex;
                    width: 100px;
                    
                    img {
                        margin-right: 10px;
                    }
                }
            }
        }
    }
}
</style>