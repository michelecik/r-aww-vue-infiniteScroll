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
    align-items: center;
    max-width: 900px;
    text-align: left;
    padding: 50px;
    height: 400px;
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
        width: 400px;
        height: 100%;
        object-fit: cover;
    }
}

@media (max-width: 768px) {
    .redditListItem {
        height: auto;
        min-height: 300px;
        flex-direction: column;
        padding: 50px;
        width: 80%;

        &__image {
            width: 100%;
        }
    }
}
</style>