<template>
    <div id="app">
        <!--<Header ref="header" title="Can" v-on:titleChanged="titleChanged"></Header>-->
        <!--<input type="text" v-model="$store.state.username">-->
        <button v-on:click="changeHeaderTitle">Select</button>

        <div v-if="datas !== null">

            <ul>
                <li v-for="(data, i) in datas">
                    {{i}}.item {{data.title}}
                </li>
            </ul>

        </div>

        <div v-else>
            Loading...
        </div>

    </div>
</template>

<style lang="stylus">

</style>

<script>
    import Header from './components/Header'

    export default {
        name: 'App',
        data() {
            return {
                inputText: '',
                datas: null
            }
        },
        methods: {
            changeHeaderTitle() {
                this.datas.splice(0, 30);
            },
            titleChanged(title) {
                alert(title);
            }
        },
        async mounted() {
            try {
                let result = await this.$axios.post('https://jsonplaceholder.typicode.com/todos', {
                    ilker: 'sa'
                });
                setTimeout(() => {
                    this.datas = result.data;
                }, 1000);
            } catch (e) {
                console.log(e);
            }
        },
        components: {
            Header
        }
    }
</script>

