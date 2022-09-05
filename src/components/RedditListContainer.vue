<template>
    <div class="">
        <RedditListItem
            v-for="item in items"
            v-bind:key="item.data.index"
            :title="item.data.title"
            :thumbnail="item.data.thumbnail"
            :link="'https://www.reddit.com' + item.data.permalink"
            :subreddit="item.data.subreddit_name_prefixed"
        />
    </div>
</template>

<script>
import RedditListItem from "./RedditListItem.vue";
import { reactive, ref } from "vue";
export default {
    name: "RedditListContainer",
    components: {RedditListItem},
    props: ["items"],
};
</script>

<style>

</style>