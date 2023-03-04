<template>
  <div>
    <v-app-bar elevation="0">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>EveryBook</v-toolbar-title>
      <v-text-field prepend-icon="mdi-magnify" label="Search" variant="underlined" clearable hide-details="auto"
        solo></v-text-field>
      <v-spacer></v-spacer>


    </v-app-bar>
    <v-divider></v-divider>

    <v-navigation-drawer>
      <v-divider></v-divider>
      <v-list>
        <v-list-item v-for="item in items" :key="item.title" link>

          <v-icon class="mx-5">{{ item.icon }} </v-icon>{{ item.title }}

        </v-list-item>
      </v-list>

      <template v-slot:append>
        <div class="pa-2">
          <v-btn block>
            Logout
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-spacer></v-spacer>
    <v-spacer></v-spacer>
    <v-container fluid>
      <v-row>
        <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
          <v-card>
            <v-img :src="card.src" class="align-end" gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)" height="250px"
              cover>
              <v-card-title class="text-white" v-text="card.title"></v-card-title>
            </v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn @click.stop="dialog = true" size="small" color="surface-variant" variant="text"
                icon="mdi-download"></v-btn>
              <v-btn size="small" color="surface-variant" variant="text" icon="mdi-heart" icon-color="red"></v-btn>
            </v-card-actions>
          </v-card>
          <v-spacer></v-spacer>
        </v-col>
        <v-spacer></v-spacer>
        <v-dialog v-model="dialog" max-width="320">
          <v-card>
            <v-card-text>
              Your book is added to your libray !
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="dialog = false">
                Close
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>

    </v-container>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      items: [
        { title: 'Library', icon: 'mdi-book-open' },
        { title: 'Account', icon: 'mdi-account-box' },
        { title: 'Admin', icon: 'mdi-gavel' },
      ],
      cards: [
        { title: 'Book 1', src: 'https://cdn.vuetifyjs.com/images/cards/house.jpg', flex: 2 },
        { title: 'Book 2', src: 'https://cdn.vuetifyjs.com/images/cards/road.jpg', flex: 2 },
        { title: 'Book 3', src: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg', flex: 2 },
      ],
      dialog: false,
    }
  },
}
</script>
