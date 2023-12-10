<script setup>
    const {movies} = defineProps(['movies']);
</script>

<template>
    <header id="header" :movies="movies">
        <div class="contain">
            <!-- <img src="https://image.tmdb.org/t/p/xgGGinKRL8xeRkaAR9RMbtyk60y.jpg" alt=""> -->
            <div class="header__inner">
                <h1><a href="/">Mega Movie</a></h1>
                <!-- <nav>
                    <ul>
                        <li><a href="/">넷플릭스</a></li>
                        <li><a href="/">디즈니</a></li>
                        <li><a href="/">애플TV</a></li>
                    </ul>
                </nav> -->
            </div>
        </div>
    </header>
</template>

<style lang="scss">
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
</style>