<template>
  <div class="home" :style="dynamicStyles">
    <h1 :style="{ color: styleColor }">Hello world!</h1>
    <ul>
      <li><a :href="link1">Home</a></li>
      <li><a :href="link2">About</a></li>
      <li><a :href="link3">Contact</a></li>
    </ul>
    <img v-bind:src="image" alt="image"><br>
    <input type="number" v-model="actionNumber">
  </div>
</template>

<script>
export default {
  data() {
    return {
      link1: "https://www.google.com",
      link2: "https://www.youtube.com",
      link3: "https://www.telegram.org",
      image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcROMGcJkDx3GyrAM8oPZRJU71ALzCE9Nfnyag&s",
      actionNumber: 0,
    };
  },
  computed: {
    dynamicStyles() {
      const n = this.actionNumber;
      return {
        'background-color': n > 50 ? "grey" : "teal",
        'font-size': n > 50 ? "24px" : "16px",
        'padding': n > 50 ? "20px" : "10px",
        'border': n > 50 ? "2px solid red" : "none"
      };
    },
    styleColor() {
      const n = this.actionNumber;
      return n >= 50 ? "orange" : "green";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
