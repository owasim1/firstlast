<template>
  <div class="text-center">
    <v-dialog persistent v-model="this.is_shown" width="500">
      <v-card>
        <v-card-title primary-title>
          Initials
        </v-card-title>
          <div class="margin" v-for="(initial, index) in initials" :key="index">
            <v-avatar class="white--text" v-if="index >= 4" color="primary">
              {{ initial.toUpperCase() }}
            </v-avatar>
          </div>
          <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" @click="hide_list" text>
            Done
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    name: 'InitialsListModal',
    props: ["is_shown", "initials",],
    data () {
      return {
        show_list: false,
      }
    },
    methods: {
      onAddInitialClick (value) {
        this.num = value
      },
      hide_list () {
        this.$emit('InitialListModalToApp', this.show_list)
      },
    }
  }
</script>

<style>
  .margin{
    margin-left: 20px;
    margin-bottom: 15px;

  }
</style>
