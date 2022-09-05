<template>
    <nav class="nav">
       <a href="https://www.reddit.com/r/aww"> r/aww </a> <img class="nav__image" src="@/assets/logo.jpg" alt="" srcset="">
    </nav>
    <RedditListContainer :items="data" />
    <h3 class="loading" v-if="loading">Loading 25 more r/aww posts...</h3>
</template>

<script>
import { onMounted, ref } from "vue";
import RedditListContainer from "./components/RedditListContainer.vue";

export default {
    name: "App",
    components: {
        RedditListContainer
    },
    setup() {
        const loading = ref()
        const data = ref([]);
        const after = ref('')

        const fetchData = () => {
            loading.value = true
            fetch(`https://www.reddit.com/r/aww.json?limit=24&after=${after.value}`)
                .then((res) => res.json())
                .then((body) => {
                    loading.value = false
                    body.data.children.forEach(item => {
                        data.value.push(item)
                    });

                    console.log(body.data.after)
                    after.value = body.data.after
                });
        };

        const fetchMoreData = () => {
            loading.value = true
            fetch(`https://www.reddit.com/r/aww.json?limit=5&after=${after.value}`)
                .then((res) => res.json())
                .then((body) => {
                    after.value = body.data.after
                    
                    loading.value = false
                    body.data.children.forEach(item => {
                        data.value.push(item)
                    });
                });
        }


        window.addEventListener('scroll', () => {
            let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;

            if(bottomOfWindow) {
                fetchData()
            }
        })

        onMounted(() => {
            fetchData()
        })

        return {
            data,
            loading
        };
    },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap');

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-family: 'Patrick Hand', cursive;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

.loading {
    margin: auto;
}

.nav {
    position: fixed;
    display: flex;
    align-items: center;
    justify-content: space-between;
    top: 30px;
    right: 30px;
    width: 100px;

    &__image {
        width: 50px;
        border-radius: 100%;
    }
}
</style>
