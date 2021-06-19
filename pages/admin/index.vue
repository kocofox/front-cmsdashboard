<template>
  <div>
    datos estadisticos
    <v-row>
      <v-col cols="12" sm="7">
        <v-row>
          <v-col>
            <v-card class="mx-auto" max-width="344" outlined>
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="text-overline mb-4">OVERLINE</div>
                  <v-list-item-title class="text-h5 mb-1">
                    Headline 5
                  </v-list-item-title>
                  <v-list-item-subtitle
                    >Greyhound divisely hello coldly
                    fonwderfully</v-list-item-subtitle
                  >
                </v-list-item-content>

                <v-list-item-avatar
                  tile
                  size="80"
                  color="grey"
                ></v-list-item-avatar>
              </v-list-item>

              <v-card-actions>
                <v-btn outlined rounded text> Button </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col>
            <v-card class="mx-auto" max-width="344" outlined>
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="text-overline mb-4">OVERLINE</div>
                  <v-list-item-title class="text-h5 mb-1">
                    Headline 5
                  </v-list-item-title>
                  <v-list-item-subtitle
                    >Greyhound divisely hello coldly
                    fonwderfully</v-list-item-subtitle
                  >
                </v-list-item-content>

                <v-list-item-avatar
                  tile
                  size="80"
                  color="grey"
                ></v-list-item-avatar>
              </v-list-item>

              <v-card-actions>
                <v-btn outlined rounded text> Button </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
      <v-col cols="12" sm="5"> <v-calendar> </v-calendar> </v-col
    ></v-row>
  </div>
</template>
<script>
export default {
  layout: 'dashboard',
  name: 'homej',
  //   head: {
  //     title: 'Home',
  //     meta: [
  //       {
  //         hid: 'description',
  //         name: 'Home',
  //         content: 'Home page description'
  //       }
  //     ],
  //   },
  beforeRouteEnter(to, from, next) {
    to.meta.title = 'Inicio'
    next()
  },
  data() {
    return {
      enableMini: true,
    }
  },

  // mounted() {
  //     console.log(this.$metaInfo.meta)
  // },
}
</script>