<template>
    <div class="redditListItem">
        <img class="redditListItem__image" :src="thumbnail" alt="" srcset="" />
        <div class="redditListItem__contentWrapper">
            <h1 class="redditListItem__title">
                <a :href="link" class="redditListItem__link" target="_blank">{{  title  }}</a>
            </h1>

            <small class="redditListItem__sub">{{subreddit}}</small>
        </div>

    </div>
</template>

<script>

export default {
    name: "RedditListItem",
    props: ['title', 'link', 'thumbnail', 'subreddit'],
    setup() {
    },
};
</script>

<style lang="scss">
.redditListItem {
    margin: 5em auto;
    display: flex;
    max-width: 900px;
    height: 200px; 
    text-align: left;
    padding: 50px;
    border-radius: 20px;

    &:hover {
        background-color: rgba(245, 199, 49, 0.1);
    }

    &__title {
        margin: 0;
    }

    &__link {
        text-decoration: none;
        color: #333;
    }

    &__contentWrapper {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin: 0 2em;
        height: 100%;
        width: 100%;
    }

    &__image {
        width: 200px;
        height: 100%;
        object-fit: cover;
    }
}
</style>