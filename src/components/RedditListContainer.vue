<template>
        <RedditListItem
            v-for="item in items"
            v-bind:key="item.data.index"
            :title="item.data.title"
            :thumbnail="item.data.thumbnail"
            :link="'https://www.reddit.com' + item.data.permalink"
            :subreddit="item.data.subreddit_name_prefixed"
        />
</template>

<script>
import RedditListItem from "./RedditListItem.vue";

export default {
    name: "RedditListContainer",
    components: {RedditListItem},
    props: ["items"],
};
</script>

<style>

</style>