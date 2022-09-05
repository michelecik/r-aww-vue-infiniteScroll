<template>
    <div class="redditListContainer">
        <RedditListItem v-for="item in items" v-bind:key="item.data.index" :item="item.data" :title="item.data.title" :thumbnail="item.data.thumbnail" :link="'https://www.reddit.com' + item.data.permalink" :subreddit="item.data.subreddit_name_prefixed" />
    </div>
</template>

<script>
import RedditListItem from "./RedditListItem.vue";
import { reactive, ref } from "vue";
export default {
    name: "RedditListContainer",
    components: {RedditListItem},
    props: ["items"],
    setup(props) {

    },
};
</script>

<style scoped lang="scss">
.redditListContainer {
}
</style>