<template>
    <h1>r/aww</h1>
    <h3 v-if="loading">Loading</h3>
    <RedditListItem v-for="item in data" v-bind:key="item.data.index" :item="item.data" />
</template>

<script>
import { ref } from "vue";
import RedditListItem from "./components/RedditListItem.vue";

export default {
    name: "App",
    components: {
        RedditListItem,
    },
    setup() {
        const loading = ref()

        const data = ref();
        const fetchData = () => {
            loading.value = true
            fetch("https://www.reddit.com/r/aww.json")
                .then((res) => res.json())
                .then((body) => {
                    loading.value = false
                    console.log(body);
                    data.value = body.data.children;
                });
        };

        fetchData();

        return {
            data,
            loading
        };
    },
};
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
