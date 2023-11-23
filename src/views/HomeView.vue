<script setup>
  import {onMounted, ref} from 'vue';
  import axios from 'axios';

  const movies = ref([]);
  const searchQuery = ref('');

  const fetchMovies = async(category) => {
    let url = 'https://api.themoviedb.org/3/movie/popular'
    switch(category){
      case 'latest':
        url = 'https://api.themoviedb.org/3/movie/now_playing';
        break;
      case 'popular':
        url = 'https://api.themoviedb.org/3/movie/popular'
        break;
      case 'upcoming':
        url = 'https://api.themoviedb.org/3/movie/upcoming'
        break;
      case 'top_rated':
        url = 'https://api.themoviedb.org/3/movie/top_rated'
        break;
    }
    try {
      const response = await axios.get(url, {
        params: {
          api_key: '77d1b9c8837fcc9ff99fabead0d2ba9b',
          language: 'ko-KR',
          page: '1'
      }
      });
        // console.log(response)
        movies.value = response.data.results;
        console.log(movies)
    } catch(err){
      console.log(err)
    }
  }
  const searchMovies = async () => {
    if(searchQuery.value.trim() !== '') {
      try {
        const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: '77d1b9c8837fcc9ff99fabead0d2ba9b',
            language: 'ko-KR',
            query: searchQuery.value,
            page: '1'
          }
        })
        movies.value = response.data.results;
      } catch(err){
        console.error(err)
      }
    } else {
      await fetchMovies('popular')
    }
  };

  onMounted(async () => {
    // 초기 페이지 로딩 시 최신 영화를 가져옴
    await fetchMovies('latest');
  });


</script>
 
<template>
  <main>
    <div class="container">
      <div class="movie__inner">
        <section class="movie__search">
          <h2 class="blind">검색하기</h2>
          <input v-model="searchQuery" type="search" placeholder="검색어를 입력해주세요" @keyup.enter="searchMovies">
          <button type="submit" @click="searchMovies">검색</button>
        </section>
        <!-- //movie__search -->
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
          <!-- //movie__tag -->
          <section class="movie__cont">
            <h2 class="blind">영화</h2>
            <div class="movie" v-for="movie in movies" :key="movie.id">
              <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title">
            </div>
          </section>
          <!-- //movie__cont -->
      </div>
      <!-- //movie__inner -->
    </div>
  </main>
</template>

<style lang="scss">
.movie__search {
  margin: 40px 0 20px;
  position: relative;

  input {
    border: 1px solid var(--black);
    padding: 1rem 2rem;
    width: 100%;
    border-radius: 50px;
  }
  button {
    position: absolute;
    right: 6px;
    top: 7px;
    width: 40px;
    height: 40px;
    background-color: var(--black);
    color: var(--white);
    border-radius: 50%;
  }
}
.movie__tag {
  ul {
    display: flex;
    li {
    a {
      border: 1px solid var(--black);
      padding: 0.5rem 1.3rem;
      display: inline-block;
      border-radius: 50px;
      margin: 20px 10px 20px 0;

      &:hover {
        background-color: var(--black);
        color: var(--white);
      }
    }
  }
  }

}
.movie__cont {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  background-color: var(--black);

  .movie {
    width: 24%;
    margin-bottom: 1%;
  }
}
</style>