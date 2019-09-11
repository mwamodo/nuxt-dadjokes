<template>
  <div>
    <h1>Jokes</h1>
    <SearchJokes v-on:search-text="searchText" />
    <Joke :key="joke.key" v-for="joke in jokes" :id="joke.id" :joke="joke.joke" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/joke";
import SearchJokes from "../../components/SearchJokes";

export default {
  components: {
    Joke,
    SearchJokes
  },
  data() {
    return {
      jokes: []
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);
      this.jokes = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: "Dad Jokes",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best Place for Dad jokes"
        }
      ]
    };
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };
      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        );
        this.jokes = res.data.results;
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>

<style>
</style>