<template>
  <v-app>
    <!-- <v-app-bar
      app
      color="secondary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar> -->
    <v-app-bar app>
      <v-img :src="require('./assets/BASF-Logo_bw.png')" max-height="48" max-width="200" contain></v-img>
      <span>BASF Moldflow udbs</span>
      <v-spacer></v-spacer>
      <v-icon class="mdi mdi-account"></v-icon><span class="ml-1">{{ user }}</span>
      
    </v-app-bar>
    <v-main class="v-wrapper">
        <v-alert
          border="left"
          color="blue"
          dismissible
          icon="mdi-human-greeting"
          type="success"
          dense
          :value="welcome_alert_toggle"
          transition="scroll-y-transition"
        >Welcome to the system, {{ user }}</v-alert>
      <!-- <HelloWorld/> -->
      <v-container>

         <v-select
          :items="materials"
          label="Standard"
          v-model="itemSelected"
          item-text="type"
          item-value="id"
          return-object
          @change="selectItem"
        ></v-select>

        <!-- custom v-list -->
        <selectedList :list="selectedItems" @delItem="removeSelectedItem"></selectedList>

      </v-container>
      <v-btn elevation="2">click me</v-btn>
    </v-main>
  </v-app>
</template>

<script>
  // import HelloWorld from './components/HelloWorld';
  import selectedList from'./components/selectedList';

  export default {
    name: 'App',

    components: {
      selectedList,
    },

    data: () => ({
      user: 'Jeffrey Wu',
      welcome_alert_toggle: true,
      materials: [
          {id: '001', type: 'Silver'},
          {id: '002', type: 'Gold'},
          {id: '003', type: 'Bronze'},
          {id: '004', type: 'Steel'},
        ],
      itemSelected: {},
      selectedItems: []
    }),
    created() {
      this.autoDismissWelcomeAlert();
    },
    methods: {
      removeSelectedItem(value) {
        this.selectedItems = this.selectedItems.filter(item => item.id !== value);
      },
      selectItem() {
        this.selectedItems.push(this.itemSelected);
      },
      autoDismissWelcomeAlert() {
        setTimeout(() => {
          this.welcome_alert_toggle = false;
        }, 5000)
      }
    }
  };
</script>
<style scoped lang="scss">
  @import './styles/variables.scss';

  .v-wrapper {
    font-size: $font-size-root;
  }
</style>