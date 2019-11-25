<template>
  <v-app>
    <h3>Name Initials</h3>
    <v-container fluid>
    <v-row>
      <v-col md="auto" v-for="(initial, index) in initials" :key="index">
        <div v-if="index < 4">
          <v-avatar class="white--text" color="primary">
            {{ initial.toUpperCase() }}
          </v-avatar>
        </div>
        <div v-if="index === 4" >
          <v-btn @click="is_shown=true" icon x-large outlined color="primary">
            +{{ number - 4 }}
          </v-btn>
        </div>
      </v-col>
    </v-row>
    <v-row>
      <InitialsListModal  v-on:InitialListModalToApp="on_hide_button"
                          :initials="initials"
                          :is_shown="is_shown"/>
      <NameFields v-on:nameFieldsToApp="on_add_initial_click" :initials="initials"/>
    </v-row>
  </v-container>
  </v-app>
</template>

<script>
import NameFields from './components/NameFields';
import InitialsListModal from './components/InitialsListModal';

export default {
  name: 'App',
  components: {
    NameFields,
    InitialsListModal,
  },
  data: () => ({
    initials: [],
    number: 0,
    is_shown: false,

  }),
  methods: {
    on_add_initial_click (value) {
      this.number = value
    },
    on_hide_button (value) {
      this.is_shown = value
    },
  }
};
</script>

<style>
#app{
  padding-left: 20px;
  padding-top: 10px;
}
</style>
