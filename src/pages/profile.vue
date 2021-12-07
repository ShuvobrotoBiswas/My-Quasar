<template>
  <q-page padding>
    <!-- content -->
    <div class="column justify-center items-center">
    <h3>{{ character.name}}</h3>
    <q-card class="my-card">
      <img :src="character.img" alt="" @click="alert = true"/>
      <q-card-section>
        <div class="text-h6">{{ character.name }}</div>
        <div class="text-subtitle2">{{ character.nickname }}</div>
      </q-card-section>
      <q-card-section>
        <q-chip
        v-for="occupation in character.occupation"
        color="teal"
        :key="occupation"
        text-color="white"
        icon="bookmark"
        >
        {{ occupation }}
        </q-chip>
      </q-card-section>
    </q-card>
    </div>
    <q-dialog v-model="alert">
     <q-card>
       <q-card-section>
         <div class="text-h6">Birthday Info</div>
       </q-card-section>
       <q-card-section align="right">
         {{ character.birthday }}
       </q-card-section>
       <q-card-actions>
         <q-btn flat label="OK" color="primary" v-close-popup></q-btn>
       </q-card-actions>
     </q-card>
    </q-dialog>
  </q-page>
</template>

<script>
import { QSpinnerCube } from "quasar";
export default {
 async created() {
   this.$q.loading.show({
     message: "Loading",
     spinnerColor: "blue",
     spinner: QSpinnerCube
   });
  let url = `https://www.breakingbadapi.com/api/characters/${this.$route.params.id}`;
  if (this.$route.params.id === 'random'){
     url = `https://www.breakingbadapi.com/api/character/${this.$route.params.id}`;
  }
  const character = await this.$axios.get(url);
  setTimeout(()=> {
    this.$q.loading.hide();
  }, 400);
   console.log(character.data);
   this.character = character.data[0];
 },
 data() {
   return {
     character: "",
     alert: false
   };
 }

  // name: 'PageName'
}
</script>
<style lang="scss" scoped>
.my-card {
  width: 20%;
}
</style>

