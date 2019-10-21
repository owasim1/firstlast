<template>
  <div class="c-name-fields">
    <v-bottom-sheet v-model="sheet">
      <template v-slot:activator="{ on }">
        <v-btn v-on="on">Add Initials</v-btn>
      </template>
      <v-sheet class="text-center" height="250px">
        <v-btn
          class="mt-6"
          flat
          color="red"
          @click="sheet = !sheet"
        >close</v-btn>
        <div>
          <v-container >
            <v-row>
              <v-col>
                <v-text-field label="First Name" outlined="true"> </v-text-field>
              </v-col>
              <v-col>
                <v-text-field label="Last Name" outlined="true"> </v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col align="right">
                <v-btn>Add</v-btn>
              </v-col>
            </v-row>
          </v-container>
        </div>
      </v-sheet>
    </v-bottom-sheet>

  </div>
</template>

<script>
export default {
  name: 'NameFields',
  props: {
  },
  data: () => ({
      sheet: false,
    }),

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.c-name-fields {
  margin-top: 10px;
}
</style>
