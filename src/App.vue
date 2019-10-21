<template>
  <v-app>
    <h3>Name Initials</h3>
    <v-list>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title>Single-line item</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title>Single-line item</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <NameFields/>
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
    //
  }),
};
</script>

<style>
</style>
