<template>
  <div >
      <h1>Selectionner les options d'impression</h1>
      <h2>Papier</h2>
      <input type="radio" value="Mat" id="Mat" name="radio1" v-model="papierSelected" :disabled="validate === true"/>
      <span for="Mat">Mat</span>
      <input type="radio" value="Brillant" id="Brillant" name="radio1" v-model="papierSelected" :disabled="validate === true">
      <span for="Brillant">Brillant</span>
      <br/>
      <h3>Taille du papier</h3>
      <select v-model="selected" :disabled="validate === true">
        <option disabled value="">Selectionner la taille</option>
        <option v-for="option in options" v-bind:key="option.text" v-bind:value="option.value">
          {{ option.text }}
        </option>
      </select>
      <span>Taille sélectionné : {{selected}}</span>
      <br/>

      <h3 class="col">Verso</h3>
      <br/>
      <input type="checkbox" id="Date" value="Date" v-model="datePhoto" :disabled="validate === true">
      <label for="Date">Date d'impression</label>
      <br/>
      <input type="checkbox" id="NomPhoto" value="NomPhoto" v-model="NomPhoto" :disabled="validate === true">
      <label for="NomPhoto">Nom de la photo</label>
      <br/>

      <input type="checkbox" id="Msg" value="Msg" v-model="msg" :disabled="validate === true">
      <label for="Msg">Message personnalisé</label>
      <br/>

      <input type="text" v-model="textVerso" :disabled="msg !== true || validate === true">

      <br/>
      <input type="button" value="Valider" @click="validate = true" :disabled="validate === true"/>
  </div>
</template>


<script>
export default {
  name: 'Configuration',
  data: function(){
    return{
      selected : undefined,
      papierSelected : undefined,
      datePhoto : undefined,
      nomPhoto : undefined,
      msg : undefined,
      textVerso : undefined,
      validate : undefined,
      options: [
        { text: '10*15', value: '10*15' },
        { text: '11*15', value: '11*15' },
        { text: 'A4', value: 'A4' },
        { text: 'A5', value: 'A5' }
      ]
    };

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.col {
  display: inline-block;
  margin: 5px;
}
div[disabled]
{
  pointer-events: none;
  opacity: 0.6;
}
</style>
