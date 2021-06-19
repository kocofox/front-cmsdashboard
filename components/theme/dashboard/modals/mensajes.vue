<template>
  <v-form ref="form">
    <v-container>
      <v-card class="mx-auto" outlined>
        <v-list-item three-line>
          <v-list-item-content>
            <div class="text-overline mb-4">{{ item.razonSocial }}</div>
            <v-list-item-title class="text-h4 mb-1">
              {{ item.asunto }}
            </v-list-item-title>
          </v-list-item-content>

          <v-list-item-avatar tile size="80" > <v-icon x-large>mdi-email-outline</v-icon> </v-list-item-avatar>
        </v-list-item>
        <v-card-text class="text-h5 font-weight-bold text-justify">
          {{ item.mensaje }}
        </v-card-text>
        <v-card-actions class="text-h5 font-weight-bold ">
          <v-spacer></v-spacer>
          <p >
            {{ item.razonSocial }}  
          </p>
          <p>
            - {{ item.correo }} -
          </p>
          <p>
            {{ item.telefono }}
          </p>
        </v-card-actions>
      </v-card>
    </v-container>
  </v-form>
</template>
<script>
export default {
  components: {
    'ckeditor-nuxt': () => {
      if (process.client) {
        return import('@blowstack/ckeditor-nuxt')
      }
    },
  },
  props: ['item', 'validate'],
  data: () => ({
    banner: null,
    upbanner: null,
    editorConfig: {
      removePlugins: ['Title', 'Images'],
      // simpleUpload: {
      //   uploadUrl: 'path_to_image_controller',
      //   headers: {
      //     'Authorization': 'optional_token'
      //   }
      // }
    },
    contentHolder: '',
    category: [],
  }),
  mounted() {
    this.loadCategorias()
  },
  methods: {
    onFileChange(evt) {
      let imglogo = evt.target.files[0]
      this.item.user_id = this.$auth.user.id
      this.item.logo = imglogo
      var reader = new FileReader()

      reader.onload = (e) => {
        this.banner = e.target.result
      }
      reader.readAsDataURL(imglogo)
    },
    imglogo() {
      document.getElementById('file-logo').click()
    },
    async loadCategorias() {
      try {
        let response = await this.crud('get', 'categorias/')
        this.category = response.data.data
      } catch (error) {
        console.log(error.response.data, 'error')
      }
    },
  },
}
</script>
<style scoped>
.crud-table >>> .v-data-table__wrapper {
  overflow: hidden;
}
.image-upload > input {
  display: none;
  justify-content: center;
  align-items: center;
}
img.preview {
  max-width: 220px;
  max-height: 220px;
}
</style>
