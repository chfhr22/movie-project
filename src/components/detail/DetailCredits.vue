<template>
    <div class="credit">
        <div>
            <img v-for="(actor, index) in movieCredits.cast.slice(0, 4)" :key="index" :src="'https://image.tmdb.org/t/p/w200/' + actor.profile_path" :alt="actor.name">
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