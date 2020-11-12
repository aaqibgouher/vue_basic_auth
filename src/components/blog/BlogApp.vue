<template>
    <div>
        <div class="mt-5"></div>
        <h3>Blog</h3>
        <div class="p-2"></div>
        <div v-if="blogs">
            <div v-for="blog in blogs" :key="blog.id" class="mb-2">
                <BlogSingle :blog="blog"/>
            </div>
            <button class="btn btn-primary" @click="loadMore">Load More</button>
        </div>
        <div v-else>No Blogs available</div>
    </div>
</template>

<script>
import BlogSingle from './BlogSingle';

export default {
    name: "BlogApp",
    components: {
        BlogSingle
    },
    data() {
        return {
            blogs: [
                {
                    id: 1,
                    title: "This is blog title",
                    description: "this is a long description"
                },
                {
                    id: 2,
                    title: "This is second blog title",
                    description: "this is a long description"
                },
                {
                    id: 3,
                    title: "This is third blog title",
                    description: "this is a long description"
                }
            ]
        }
    },
    methods: {
        loadMore(){
            var blog_more = this.blogs[this.blogs.length-1];
            console.log(blog_more)
            blog_more.id = blog_more.id+1;
            this.blogs.push(blog_more);
        }
    }
}
</script>