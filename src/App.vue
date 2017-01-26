<template>
    <div id="app">
        <!-- <h2>{{ msg }}</h2>
        <ul>
            <li v-for="b in blargs" v-text="b">
        </ul>
        <input id="input" type="text" v-model="blarg">
        <button @click="blargIt" id="foo">Foo</button>
        <foobar></foobar> -->
        <wiki></wiki>
        <gif></gif>
    </div>
</template>

<script>
    import foobar from './components/Foobar.vue';
    import wiki from './components/wiki/wiki.vue';
    import gif from './components/gif/gif.vue';

    export default {
      components: {
        foobar,
        wiki,
        gif
      },
      name: 'app',
      data () {
        return {
          msg: 'Blank slate',
          blarg: '',
          blargs: []
        }
      },

      methods: {
        blargIt() {
        this.blargs.push(this.blarg);
        this.blarg = '';
        }
      }
    }

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

</style>
