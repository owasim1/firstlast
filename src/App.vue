<template>
  <v-app>
    <h3>Name Initials</h3>
    <v-list>
      <v-list-item v-for="(initial, index) in initials" :key="index">
        <v-list-item-content>
          <v-list-item-title>{{ initial.toUpperCase() }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <NameFields :initials="initials" />
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
    initials: []
  }),
};
</script>

<style>
</style>
