<template>
  <div>
    <h2>Data Fetching {{ msg }}</h2>
    <p class="joke">{{ data.joke }}</p>
    <!-- <button @click="toggleJoke()">Next Joke</button> -->
  </div>
</template>

<script>
export default {
  name: "HomePage",
  props: {
    msg: String,
  },
  data() {
    return {
      data: " ",
    };
  },
  mounted() {
    fetch("https://icanhazdadjoke.com/", {
      headers: {
        Accept: "application/json",
      },
    })
      .then((res) => res.json())
      .then((data) => (this.data = data));
  },
  // methods: {
  //   toggleJoke() {
  //     this.data = this.data.joke;
  //   },
  // },
};
</script>

<style>
.joke {
  width: 50%;
  margin: 15px auto;
  padding: 15px;
  background-color: gold;
}

button {
  padding: 5px 15px;
  text-transform: uppercase;
  font-family: inherit;
  border: 2px solid red;
  border-radius: 5px;
  background: transparent;
}

button:hover {
  background: red;
  border: 2px solid black;
  transition: 300ms;
}
</style>