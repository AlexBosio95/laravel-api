<template>
    <div class="container">

        
        <nav aria-label="Page navigation example">
            <ul class="pagination">
                <li class="page-item" :class="(currentPage == 1) ? 'disabled': '' "><a class="page-link" href="#" @click="getPagePost(currentPage - 1)">Previous</a></li>
                <li class="page-item" :class="(currentPage == lastPage) ? 'disabled': '' "><a class="page-link" href="#" @click="getPagePost(currentPage + 1)">Next</a></li>
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
        
        getPagePost(page){
            this.loadingPage = false;

            axios.get('/api/posts', {

                params: {
                        page: page
                    }
            })
            .then((response) => {
                this.ArrayPosts = response.data.results.data;
                this.currentPage = response.data.results.current_page;
                this.lastPage = response.data.results.last_page;
            });
        }
    },
    mounted(){
        this.getPagePost(1);
    }
}
</script>

<style>

</style>