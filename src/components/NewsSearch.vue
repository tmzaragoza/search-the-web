<template>
    <section>
        News Search
        <form @submit.prevent="handleSubmit">
            <input v-model="keyword" required>
            <button> Search </button>
        </form>
    </section>
</template>

<script>
export default {
    props: {
        search: String,
        onSearch: Function
    },
    data() {
        return {
            keyword: this.search || ''
        };
    },
    watch: {
        search(newSearch) {
            if(this.keyword !== newSearch) {
                this.keyword = newSearch;
            }
        }
    },
    methods: {
        handleSubmit(){
            this.$router.push({
                query: {
                    search: encodeURIComponent(this.keyword)
                }
            });
        }
    }

};
</script>

<style>

</style>
