<template>
    <div class="container">

        
        <nav aria-label="Page navigation example">
            <ul class="pagination">
                <li class="page-item" @click="(this.currentPage - 1)"><a class="page-link" href="#">Previous</a></li>
                <li class="page-item"><a class="page-link" href="#">Next</a></li>
            </ul>
        </nav>

        <div class="row">
            <Card :ArrayPosts = 'ArrayPosts'/>
        </div>

    </div>

</template>

<script>

import Card from '../components/Card.vue'

export default {
    name: 'MainPost',
    components: {
        Card
    },
    data() {
        return{
            ArrayPosts: [],
            currentPage: 1,
            lastPage: null,
            loadingPage: true,
        }
    },
    methods: {
        
        getPagePost(){
            this.loadingPage = false;

            axios.get('/api/posts')
            .then((response) => {
                this.ArrayPosts = response.data.results.data;
                this.currentPage = response.data.results.currentPage;
            });
        }
    },
    mounted(){
        this.getPagePost();
    }
}
</script>

<style>

</style>