<template>
  <div class="c-name-fields">
    <div class="text-center pad">
      <v-dialog v-model="sheet" height="800px" width="600px">
        <template v-slot:activator="{ on }">
          <v-btn v-on="on">Add Initials</v-btn>
        </template>
        <v-card class="text-center" >
          <v-btn class="mt-6" color="red" @click="sheet = !sheet">close</v-btn>
          <v-container class="text-fields" >
            <v-row>
              <v-col>
                <v-text-field width="10px" label="First Name" outlined v-model="firstNameField"> </v-text-field>
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
        </v-card>
      </v-dialog>
    </div>
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
</template>

<script>
export default {
  name: 'NameFields',
  props: ["initials",],
  data: () => ({
      nameFieldsNotEmpty: false,
      sheet: false,
      firstNameField:"",
      lastNameField:"",
      dialog: false,
      num: 0,
    }),
  methods: {
    addInitials () {
      if(this.firstNameField =="" || this.lastNameField==""){
        this.dialog = true
      }
      if(this.firstNameField!="" && this.lastNameField!=""){
        this.nameFieldsNotEmpty=true
      }
      if(this.nameFieldsNotEmpty) {
        this.initials.push(this.firstNameField[0]+this.lastNameField[0]);
        this.nameFieldsNotEmpty=false
      this.num = this.initials.length
      this.$emit('nameFieldsToApp', this.num)
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
.pad {

}
</style>
