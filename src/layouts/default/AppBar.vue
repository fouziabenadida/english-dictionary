<template>
  <v-app app>
    <v-app-bar app>
      <v-toolbar-title> Dictionary </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-list>
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
          title="Sandra Adams"
          subtitle="sandra_a88@gmailcom"
        ></v-list-item>
      </v-list>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row>
          <v-col v-for="n in 9" :key="n" cols="12">
            <v-card>
              <v-row>
                <v-col>
                  <v-card-title>Hapiness</v-card-title>
                </v-col>

                <v-col v-if="showInput">
                  <v-card-text >5</v-card-text>
                </v-col>
                <v-col v-else >
                  <v-text-field density="compact"   class="pa-0 mt-4 pr-2" variant="outlined"></v-text-field>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col align="end">
            <v-menu>
              <template v-slot:activator="{ props }">
                <v-btn
                  v-if="showButton1"
                  class="scroll-button"
                  v-bind="props"
                  rounded
                  style="border-radius: 50%"
                  icon="mdi-dots-vertical"
                >
                </v-btn>
                <v-btn
                  v-else
                  class="scroll-button"
                  style="border-radius: 50%"
                  icon="mdi-send"
                ></v-btn>
              </template>
              <v-list>
                <v-list-item @click="showDialog()">
                  <v-list-item-title>Yeni</v-list-item-title>
                </v-list-item>

                <v-list-item @click="changeButton(); changeInput()">
                  <v-list-item-title>Test</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>
          </v-col>
        </v-row>
        <v-row>
          <CreateNewWord
            v-model="openDialog"
            @cancelDialog="openDialog = false"
          />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import CreateNewWord from "../../components/dialogs/CreateNewWord.vue";
export default {
  components: {
    CreateNewWord,
  },
  data() {
    return {
      items: [{ title: "Yeni" }, { title: "Test" }],
      openDialog: false,
      test: false,
      showButton1: true,
      showInput: true
    };
  },
  methods: {
    showDialog() {
      this.openDialog = true;
    },
    changeButton() {
      this.showButton1 = !this.showButton1;
    },
    changeInput() {
    this.showInput= !this.showInput;
    }
  },
};
</script>

<style>
.custom-class {
  background: rgb(var(--v-theme-something));
  color: rgba(var(--v-theme-on-something), 0.9);
}
.scroll-button {
  position: fixed;
  bottom: 20px;
  background: purple;
  right: 20px;
  opacity: 10;
  transition: opacity 0.3s ease;
}
.send-btn {
}
</style>
