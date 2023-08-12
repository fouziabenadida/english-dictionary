<template>
  <v-dialog v-model="showDialog" transition="dialog-bottom-transition" width="400">
    <v-card>
      <v-card-title class="headline black" primary-title>
        New Word
      </v-card-title>
      <v-card-text class="pa-5">
        <v-form>
          <v-col>
            <v-text-field outlined hide-details></v-text-field>
          </v-col>
          <v-col>
            <v-select outlined hide-details label="Type"></v-select>
          </v-col>
          <v-col>
            <v-textarea></v-textarea>
          </v-col>
          <v-card-actions class="pa-5">
            <v-btn class="ml-auto" @click="closeDialog()" outlined color="red"
              >Cancel</v-btn
            >
            <v-btn class="mx-2" outlined color="primary"
              >Save</v-btn
            >
          </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>
<script lang="ts">
export default {
  name: "CreateNewWord",
  emits: ["cancelDialog"],
  data() {
    return {
        showDialog: false,
    };
  },
  methods: {
    closeDialog() {
        this.showDialog = false;
        this.$emit("cancelDialog", false)
    }
  },
};
</script>
