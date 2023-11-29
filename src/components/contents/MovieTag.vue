<template>
    <div class="movie__tag">
        <ul>
            <li><a href="#" @click="fetchMovies('latest')">최신 영화</a></li>
            <li><a href="#" @click="fetchMovies('popular')">인기 영화</a></li>
            <li><a href="#" @click="fetchMovies('top_rated')">최고 평점</a></li>
            <li><a href="#" @click="fetchMovies('upcoming')">개봉 예정</a></li>
            <!-- <li><a href="#">공포영화</a></li>
            <li><a href="#">액션영화</a></li>
            <li><a href="#">슬픈영화</a></li> -->
        </ul>
    </div>
</template>