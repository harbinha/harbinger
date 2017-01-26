<template>
    <div id="gif">
        <h2>Mandatory random gif</h2>
        <input type="text" name="gif" placeholder="gif it" v-model="gifit" @keyup.enter="randomize">
        <button @click="randomize">get a gif</button>
        <button @click="clear">stop</button>
        <a v-if="gif" :href="gif.url">
            <img v-if="gif" :src="gif.image_url" class="gif">
        </a>
    </div>
</template>

<script>
    export default{
        name: 'gif',
        data() {
            return {
                gif: '',
                gifit: ''
            }
        },
        methods: {
            randomize() {
                let tag = this.gifit ? this.gifit : 'star+wars';
                fetch('http://api.giphy.com/v1/gifs/random?api_key=dc6zaTOxFJmzC&tag=' + tag).then(response => {
                    this.gif = {};
                    response.json().then(resp => {
                        this.gif = resp.data;
                    })
                })
            },

            clear() {
                this.gif = {};
            }
        }
    }
</script>

<style>
    #gif {
        margin: 30px 0;
    }
    .gif {
        display: block;
        height: auto;
        max-height: 400px;
        max-width: 400px;
    }
</style>
