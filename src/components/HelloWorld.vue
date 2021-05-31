<template>
  <form action="save()">
    <h1>Meine TODO-Liste</h1>
    <div id="aufgabe">
      <label for="aufgabe">Aufgabe</label>
      <input type="text" name="aufgabe" placeholder="Do Be Do Be Do" >
    </div>
    <div id="erledigt_bis">
      <label for="erledigt">erledigt bis</label>
      <input type="text" name="erledigt" placeholder="Do Be Do Be Do" >
    </div>
    <div id="kategorie">
      <label for="kategorie">Kategorie</label>
      <select name="kategorie">
        <option value="Privat" selected>Privat</option>
        <option value="Arbeit">Arbeit</option>
        <option value="Schule">Schule</option>
      </select>
    </div>
  </form>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    msg: String
  }
})
export default class HelloWorld extends Vue {
  msg!: string
}
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
