<script setup>
  // import {onMounted, ref} from 'vue';
  // import axios from 'axios';

  // const movies = ref([]);
  // const searchQuery = ref('');

  // const fetchMovies = async(category) => {
  //   let url = 'https://api.themoviedb.org/3/movie/popular'
  //   switch(category){
  //     case 'latest':
  //       url = 'https://api.themoviedb.org/3/movie/now_playing';
  //       break;
  //     case 'popular':
  //       url = 'https://api.themoviedb.org/3/movie/popular'
  //       break;
  //     case 'upcoming':
  //       url = 'https://api.themoviedb.org/3/movie/upcoming'
  //       break;
  //     case 'top_rated':
  //       url = 'https://api.themoviedb.org/3/movie/top_rated'
  //       break;
  //   }
  //   try {
  //     const response = await axios.get(url, {
  //       params: {
  //         api_key: '77d1b9c8837fcc9ff99fabead0d2ba9b',
  //         language: 'ko-KR',
  //         page: '1'
  //     }
  //     });
  //       // console.log(response)
  //       movies.value = response.data.results;
  //       console.log(movies)
  //   } catch(err){
  //     console.log(err)
  //   }
  // }
  // const searchMovies = async () => {
  //   if(searchQuery.value.trim() !== '') {
  //     try {
  //       const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
  //         params: {
  //           api_key: '77d1b9c8837fcc9ff99fabead0d2ba9b',
  //           language: 'ko-KR',
  //           query: searchQuery.value,
  //           page: '1'
  //         }
  //       })
  //       movies.value = response.data.results;
  //     } catch(err){
  //       console.error(err)
  //     }
  //   } else {
  //     await fetchMovies('popular')
  //   }
  // };

  // onMounted(async () => {
  //   // 초기 페이지 로딩 시 최신 영화를 가져옴
  //   await fetchMovies('latest');
  // });


</script>
 
<template role="banner">
  <HeaderSection />

  <main id="main" role="main">
    <div class="container">
      <div class="movie__inner">
        
        <MovieSearch @onSearch="'search'"/>
        <!-- //movie__search -->
        
        <MovieTag @onSearch="'tags'"/>
          <!-- //movie__tag -->
        
        <MovieCont />
          <!-- //movie__cont -->
      </div>
      <!-- //movie__inner -->
    </div>
  </main>
  
  <FooterSection />
  
</template>

<script>
  import HeaderSection from '@/components/section/HeaderSection.vue'
  import FooterSection from '@/components/section/FooterSection.vue'

  import MovieSearch from '../components/contents/MovieSearch.vue';
  import MovieTag from '../components/contents/MovieTag.vue';
  import MovieCont from '../components/contents/MovieCont.vue';

  export default {
    name: "Movie HomePage",
    components: {
      HeaderSection,
      FooterSection,
      MovieSearch,
      MovieTag,
      MovieCont
    },
    data(){
      return {
        movies: [],
      }
    },
    methods: {
      async search(query){
        try {
          const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=77d1b9c8837fcc9ff99fabead0d2ba9b&language:ko-KR&query=${query}`)
          const result = await response.json();
          console.log(result);
        } catch (error) {
          console.log(error)
        }
    },
      async tags(query){
        try {
          const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=77d1b9c8837fcc9ff99fabead0d2ba9b&language:ko-KR&query=${query}`)
          const result = await response.json();
          console.log(result);
        } catch (error) {
          console.log(error)
        }
    },
    }
  }
</script>

<style lang="scss">
.movie__search {
  margin: 40px 0 20px;
  position: relative;

  input {
    border: 1px solid var(--white);
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
      border: 1px solid var(--white);
      background-color: var(--black);
      color: var(--white);
      padding: 0.5rem 1.3rem;
      display: inline-block;
      border-radius: 50px;
      margin: 20px 10px 20px 0;

      &:hover {
        background-color: var(--white);
        color: var(--black);
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