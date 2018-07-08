<template>
  <v-ons-page>
    <v-ons-toolbar>
      <div class="center">Alert Dialogs</div>
    </v-ons-toolbar>

    <v-ons-list>
      <v-ons-list-header>Notifications</v-ons-list-header>
      <v-ons-list-item
        tappable
        @click="$ons.notification.alert('Hello, world!')"
        >
        <div class="center">
          Alert
        </div>
      </v-ons-list-item>
      <v-ons-list-item
        tappable
        @click="$ons.notification.confirm('Are you ready?')"
        >
        <div class="center">
          Confirmation
        </div>
      </v-ons-list-item>
      <v-ons-list-item
        tappable
        @click="$ons.notification.prompt('What is your name?')"
        >
        <div class="center">
          Prompt
        </div>
      </v-ons-list-item>

      <v-ons-list-header>Components</v-ons-list-header>

      <v-ons-list-item tappable
        @click="alertDialog1Visible = true"
      >
        <div class="center">
          Alert Dialog (slots)
        </div>
      </v-ons-list-item>

      <v-ons-list-item tappable
        @click="alertDialog2Visible = true"
      >
        <div class="center">
          Alert Dialog (props)
        </div>
      </v-ons-list-item>

    </v-ons-list>

    <v-ons-alert-dialog modifier="rowfooter"
      :visible.sync="alertDialog1Visible"
    >
      <span slot="title">Title slots</span>
      Lorem ipsum
      <template slot="footer">
        <v-ons-alert-dialog-button @click="alertDialog1Visible = false">Cancel</v-ons-alert-dialog-button>
        <v-ons-alert-dialog-button @click="alertDialog1Visible = false">Ok</v-ons-alert-dialog-button>
      </template>
    </v-ons-alert-dialog>

    <v-ons-alert-dialog modifier="rowfooter"
      :title="'Title props'"
      :footer="{
        Cancel: () => alertDialog2Visible = false,
        Ok: () => alertDialog2Visible = false
      }"
      :visible.sync="alertDialog2Visible"
    >
      Lorem ipsum
    </v-ons-alert-dialog>

  </v-ons-page>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      alertDialog1Visible: false,
      alertDialog2Visible: false
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
