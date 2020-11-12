<template>
    <div>
        <div class="border p-3">
            <h4>{{ blog.title }}</h4>
            <p>{{ blog.description }}</p>
            <p>created date 20 Nov 2020</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "BlogSingle",
    props: ["blog"]
}
</script>