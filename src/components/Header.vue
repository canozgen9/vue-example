<template>
    <div class="header">
        {{$store.state.username}}
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
    </div>
</template>


<style lang="stylus">
    .header
        padding 20px
        background-color #F00
        color #FFF
</style>

<script>
    export default {
        name: 'Header',
        props: [
            'title'
        ],
        methods: {
            changeTitle(title) {
                this.title = title;

                setTimeout(() => {
                    this.$emit('titleChanged', title);
                }, 1000);
            }
        },
        computed: {
            username() {
                return this.$store.state.username;
            }
        }
    }
</script>