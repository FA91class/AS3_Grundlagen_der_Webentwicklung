<template>
  <v-container>
    <div id="content">
      <h1>Meine TODO-Liste</h1>
      <div id="form">
        <div id="aufgabe">
          <label for="aufgabe">Aufgabe</label>
          <input type="text" id="aufgabe_in" name="aufgabe" placeholder="Do Be Do Be Do" required>
        </div>
        <div id="erledigt_bis">
          <label for="erledigt">erledigt bis</label>
          <input type="date" id="erledigt_in" name="erledigt" required>
        </div>
        <div id="kategorie">
          <label for="kategorie">Kategorie</label>
          <select name="kategorie" id="kategorie_in">
            <option value="Privat" selected>Privat</option>
            <option value="Arbeit">Arbeit</option>
            <option value="Schule">Schule</option>
          </select>
        </div>
        <button id="save" v-on:click="save()">Aufgabe Speichern</button>
      </div>
      <div id="result">
        <table id="resultTable">
        </table>
      </div>
      <div id="footer">
        <img src="data:image/png;base64,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" alt="logo">
      </div>    
    </div>
    
  </v-container>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    name: 'HelloWorld',
    methods: {
      save: function() {

        let aufgabe = document.getElementById("aufgabe_in") as HTMLInputElement
        let erledigt = document.getElementById("erledigt_in") as HTMLInputElement
        let kategorie = document.getElementById("kategorie_in") as HTMLSelectElement

        let today = new Date();
        let dd = String(today.getDate()).padStart(2, '0');
        let mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
        let yyyy = today.getFullYear();

        let day =yyyy + '-' + mm + '-' + dd;

        if (!aufgabe.value.trim().length) {
          aufgabe.value = "Be Do Be Do Be"
        }
        
        if (!Date.parse(erledigt.value)) {
          erledigt.value = day
        }

        let result: rowMow = {
            ag: aufgabe.value,
            er: erledigt.value,
            ka: kategorie.value
        }
        

        let mi = sessionStorage.getItem("si")
        let li: object[] = []

        if (mi != null) {
          li = JSON.parse(mi)
        }

        li.push(result)

        sessionStorage.clear()

        sessionStorage.setItem("si", JSON.stringify(li))

        this.loadRows()

        // target.appendChild(row)
        console.log("saved")
        
      },
      loadRows: function() { 
        
        let li: rowMow[] = [];
        let mi = ""
        let sg = sessionStorage
        let target = document.getElementById("resultTable") as HTMLTableElement

        let h = document.createElement("tr")
        let h1 = document.createElement("th")
        let h2 = document.createElement("th")
        let h3 = document.createElement("th")

        h1.innerHTML = "Aufgabe"
        h1.id = "ag"
        h1.style.borderStyle = "solid"
        h1.style.borderWidth = "thin"
        h1.style.borderColor = "grey"
        h1.style.backgroundColor = "#53777A"
        h1.style.color = "white"
        h1.style.fontWeight = "normal"
        h1.style.padding = "0.5em"
        h1.style.width = "55%"

        h2.innerHTML = "bis"
        h2.id = "bi"
        h2.style.borderStyle = "solid"
        h2.style.borderWidth = "thin"
        h2.style.borderColor = "grey"
        h2.style.backgroundColor = "#53777A"
        h2.style.color = "white"
        h2.style.fontWeight = "normal"
        h2.style.padding = "0.5em"
        h2.style.width = "22.5%"

        h3.innerHTML = "Kategorie"
        h3.id = "ka"
        h3.style.borderStyle = "solid"
        h3.style.borderWidth = "thin"
        h3.style.borderColor = "grey"
        h3.style.backgroundColor = "#53777A"
        h3.style.color = "white"
        h3.style.fontWeight = "normal"
        h3.style.padding = "0.5em"
        h3.style.width = "22.5%"

        h.appendChild(h1)
        h.appendChild(h2)
        h.appendChild(h3)

        target.innerHTML = ""
        target.appendChild(h)

        if (sg.getItem("si") != null) {
          mi = sg.getItem("si") as string
          li = JSON.parse(mi)
        }

        li.forEach(obj => {
          let row = document.createElement("tr")
          let ag = document.createElement("td")
          let er = document.createElement("td")
          let ka = document.createElement("td")

          ag.innerHTML = obj.ag
          ag.style.padding = "0.4em"
          ag.style.paddingLeft = "0.6em"
          ag.style.borderStyle = "solid"
          ag.style.borderWidth = "thin"
          ag.style.borderColor = "grey"
          er.innerHTML = obj.er
          er.style.padding = "0.4em"
          er.style.paddingLeft = "0.6em"
          er.style.borderStyle = "solid"
          er.style.borderWidth = "thin"
          er.style.borderColor = "grey"
          ka.innerHTML = obj.ka
          ka.style.padding = "0.4em"
          ka.style.paddingLeft = "0.6em"
          ka.style.borderStyle = "solid"
          ka.style.borderWidth = "thin"
          ka.style.borderColor = "grey"

          row.appendChild(ag)
          row.appendChild(er)
          row.appendChild(ka)

          target.appendChild(row)

          let aufgabe = document.getElementById("aufgabe_in") as HTMLInputElement
          let erledigt = document.getElementById("erledigt_in") as HTMLInputElement

          aufgabe.value = ""
          erledigt.value = ""
        });
      },
    },
    mounted() {
      this.loadRows()
    }    
  })

  interface rowMow {
            ag: string;
            er: string;
            ka: string;
         }

</script>

<style lang="sass" scoped>
$base-color: #D1E0E1
$sec-color: #53777A

#content  
  width: 40rem
  margin: auto
  border-style: solid
  border-width: thin 
  border-color: lightgrey

  #form
    padding: 1.5rem

    input, select, button
      border-style: solid
      border-width: thin 
      border-color: lightgrey
      display: flex
      padding: 0.1em
      padding-left: 0.5em
      margin-top: 0.5em
      margin-bottom: 0.5em

    #aufgabe
      input
        width: 35em        

    select
      width: 16em

    button
      padding-right: 0.8em
      padding-left: 0.8em
      padding-top: 0.4em
      padding-bottom: 0.4em
      background-color: $sec-color
      color: white

  h1
    padding-top: 1.5rem
    font-size: 1.8rem
    text-align: center
    background-color: $base-color
    height: 6rem

  #footer
    background-color: $base-color
    height: 5rem
    display: flex

    img
      width: 10em
      height: 3em
      align-self: center
      margin: auto

table, tr
    border-style: solid
    border-width: thin
    border-color: grey

table
  border-collapse: collapse
  width: 36rem
  margin: 1.5rem
  margin-bottom: 3rem

th
  background-color: $sec-color
  color: white
  font-weight: normal
  padding: 0.5em
</style>