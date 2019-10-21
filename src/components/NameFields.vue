<template>
  <div class="c-name-fields">
    <v-bottom-sheet v-model="sheet">
      <template v-slot:activator="{ on }">
        <v-btn v-on="on">Add Initials</v-btn>
      </template>
      <v-sheet class="text-center" height="250px">
        <v-btn class="mt-6" color="red" @click="sheet = !sheet"
        >close</v-btn>
        <div>
          <v-container class="text-fields" >
            <v-row>
              <v-col>
                <v-text-field label="First Name" outlined v-model="firstNameField"> </v-text-field>
              </v-col>
              <v-col>
                <v-text-field label="Last Name" outlined v-model="lastNameField"> </v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col align="right">
                <v-btn @click="addInitials">Add</v-btn>
              </v-col>
            </v-row>
          </v-container>
          <v-dialog class="error" v-model="dialog" width="500">
            <v-card>
              <v-card-title class="headline grey lighten-2" secondary-title>
                Error
              </v-card-title>
              <v-card-text>
                Please fill in all the fields.
              </v-card-text>
            </v-card>
          </v-dialog>
        </div>
      </v-sheet>
    </v-bottom-sheet>
  </div>
</template>

<script>
export default {
  name: 'NameFields',
  props: ["initials"],
  data: () => ({
      isValid: false,
      sheet: false,
      firstNameField:"",
      lastNameField:"",
      dialog: false,
    }),
  methods: {
    addInitials: function() {
      if(this.firstNameField =="" || this.lastNameField==""){
        this.dialog = true
      }
      if(this.firstNameField!="" && this.lastNameField!=""){
        this.isValid=true
      }
      if(this.isValid) {
        this.initials.push(this.firstNameField[0]+this.lastNameField[0]);
        this.isValid=false
      }

    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.c-name-fields {
  margin-top: 10px;
}
</style>
