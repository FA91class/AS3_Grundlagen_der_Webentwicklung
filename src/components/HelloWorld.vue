<template>
<bootstrap-vue>
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
</bootstrap-vue>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { BootstrapVue } from 'bootstrap-vue'

@Options({
  components: {
    BootstrapVue
  },
  props: {
    msg: String
  }
})
export default class HelloWorld extends Vue {
  msg!: string
}
</script>

<style lang="sass" scoped>

</style>

