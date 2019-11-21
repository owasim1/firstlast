<template>
  <v-app>
    <h3>Name Initials</h3>
    <v-container fluid>
    <v-row>
      <v-col md="auto" v-for="(initial, index) in initials" :key="index">
        <div v-if="index < 4">
          <v-avatar color="teal">
            {{ initial.toUpperCase() }}
          </v-avatar>
        </div>
        <div v-if="index === 4" >
          <v-btn icon x-large outlined color="teal">
            +{{ num - 4 }}
          </v-btn>
        </div>
      </v-col>
    </v-row>
    <v-row>
      <NameFields v-on:nameFieldsToApp="onAddInitialClick" :initials="initials"/>
    </v-row>
  </v-container>
  </v-app>
</template>

<script>
import NameFields from './components/NameFields';

export default {
  name: 'App',
  components: {
    NameFields,
  },
  data: () => ({
    initials: [],
    num: 0,

  }),
  methods: {
    onAddInitialClick (value) {
      this.num = value
    }
  }
};
</script>

<style>
#app{
  padding-left: 20px;
  padding-top: 10px;
}
</style>
