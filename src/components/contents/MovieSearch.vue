<template>
    <section class="movie__search">
        <h2 class="blind">검색하기</h2>
        <input v-model="searchQuery" type="search" placeholder="검색어를 입력해주세요" @keyup.enter="searchMovies">
        <button type="submit" @click="searchMovies">검색</button>
    </section>
</template>

<script>
export default {
    
}
</script>