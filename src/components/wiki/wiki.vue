<template>
    <div id="wiki">
        <input id="input" type="text" v-model="query" @keyup.enter="searchIt" placeholder="Search Wikipedia">
        <button id="go" @click="searchIt">Go</button>
        <div class="content">{{ data }}</div>
    </div>
</template>

<script>
    export default{
        name: 'wiki',
        data(){
            return{
                query: '',
                data: ''
            }
        },
        methods: {
            searchIt() {
                if (this.query.length > 0) {
                    console.log('getting data for: ' + this.query)
                    fetch('https://en.wikipedia.org/w/api.php?action=opensearch&format=json&redirects=resolve&limit=4&&origin=*&search=' + this.query, {method: 'GET', mode: 'cors'}).then(response => {
                        response.json().then(data => {
                            console.log(data);
                            this.data = data;
                        })
                    });
                }
            }
        }
    }
</script>

<style>
#wiki {
    margin: 30px 0;
}
</style>
