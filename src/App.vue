<template>
  <div class="app">
    <Header title="The Anime Qouter"/>
    <Qoute :qoute="qoute" />
    <div class="button-container">
      <button @click="getQoute">Generate Qoute</button>
    </div>
    <QouteList :qoutes="qoutes"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Qoute from './components/Qoute.vue'
import QouteList from './components/QouteList.vue'

export default {
  name: 'App',
  components: {
    Header, Qoute, QouteList
  },
  data(){
    return {
      qoute: {
        content: '',
        anime: '  ',
        character : ''
      },
      qoutes: []
    }
  },
  methods: {
    async getQoute() {
      if (this.qoute.content) {
        this.qoutes = [...this.qoutes, this.qoute];
      }

      const data = await fetch('https://animechan.vercel.app/api/random').then(res => res.json());
      console.log(data);

      this.qoute = {
        content: data.quote,
        anime: data.anime,
        character: data.character
      };
    }
  },
  created() {
    // this.getQoute();
  }
}
</script>

<style lang="scss">
:root {
  --primary: #D81E5B;
  --secondary: #8A4FFF;
  --tertiary: #32CBFF;
  --dark: #131A26;
  --light: #EEE;
  --grey: #848484;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

.button-container {
  display: flex;
  justify-content: center;
  padding: 0px 32px;
  margin: 64px auto;

  button {
    border: none;
    outline: none;
    background-color: var(--primary);

    padding: 16px 32px;
    border-radius: 99px;

    color: var(--light);
    font-size: 28px;
    font-weight: 700;
    text-transform: uppercase;
    cursor: pointer;
    transition: 0.4s;

    &:hover {
      background-color: var(--secondary);
    }
  }
}
</style>
