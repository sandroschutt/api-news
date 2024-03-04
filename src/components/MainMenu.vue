<template>
  <header>
    <h2 class="site-title"><a href="/">API News</a></h2>
    <ul>
      <li><a href="/sobre">Sobre</a></li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "MainMenu",
  props: {
        msg: String,
    },
};
</script>

<style scoped>
header {
  display: grid;
  grid-template-columns: auto auto;
  padding: 12px;
}

ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: end;
}

li {
  padding: 0px 8px;
  font-size: 1.2em;
  list-style: none;
  align-self: center;
}

h2 a,
li a {
  color: #000000;
}
.site-title {
  font-size: 2rem;
  font-weight: bold;
}
</style>
