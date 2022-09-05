<template>
    <div class="redditListItem">
        <img
            class="redditListItem--image"
            :src="mini.thumbnail"
            alt=""
            srcset=""
        />
        <a :href="mini.link" target="_blank">{{ mini.title }}</a>
    </div>
</template>

<script>
import { reactive } from "@vue/reactivity";
export default {
    name: "RedditListItem",
    props: ["item"],
    setup(props) {
        const mini = reactive({
            title: props.item.title,
            thumbnail: props.item.thumbnail,
            link: 'https://www.reddit.com/' + props.item.permalink
        });

        return { mini };
    },
};
</script>

<style lang="scss">
.redditListItem {
    margin: 10px auto;
    display: flex;
    width: 80%;
    border: 1px solid rebeccapurple;
}
</style>