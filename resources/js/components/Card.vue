<template>
    <div class="col-12">
        <div class="card my-4" v-for="(post, index) in ArrayPosts" :key="index">
            <div class="card-body">
                <h5 class="card-title text-center">{{post.name}}</h5>
                <p class="card-text">{{post.content}}</p>
                <p class="card-text">{{post.category?post.category.name:'-'}}</p>
                <a href="#" class="btn btn-primary">Read more</a>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    props: {
        ArrayPosts : Array
    }
}
</script>

<style>

</style>