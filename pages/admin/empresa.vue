<template>
  <div class="height-100pc">
    <v-card class="py-2 height-100pc crud-card" elevation="1">
      <v-stepper v-model="e1" >
        <v-stepper-header>
          <v-stepper-step :complete="e1 > 1" editable step="1">
            Información Básica
          </v-stepper-step>

          <v-divider></v-divider>

          <v-stepper-step :complete="e1 > 2" editable step="2">
            Nosotros
          </v-stepper-step>

          <v-divider></v-divider>

          <v-stepper-step step="3" editable> Redes Sociales </v-stepper-step>
        </v-stepper-header>

        <v-stepper-items>
          <v-stepper-content step="1" class="pa-2">
            <v-row  >
              <v-col cols="12" >
                <v-card color="#E3F2FD" flat>
                  <v-card-title> Título </v-card-title>
                  <v-card-text>
                    <v-text-field dense
                      v-model="empresa.titulo"
                      :error-messages="validate.titulo"
                      persistent-placeholder
                      outlined
                      clearable
                      rounded
                      required
                      hint="5 y 70 caracteres"
                      persistent-hint
                    ></v-text-field>
                  </v-card-text>
                </v-card> </v-col
            ></v-row>
            <v-row>
              <v-col cols="12" sm="6">
                <v-row>
                  <v-col cols="12">
                    <v-card color="#F9FBE7">
                      <v-card-title> Etiquetas </v-card-title>
                      <v-card-text>
                        <v-combobox
                        dense
                          v-model="model"
                          hide-selected
                          label="Agregar etiqueta"
                          multiple
                          small-chips
                          outlined
                        >
                          <template
                            v-slot:selection="{ attrs, item, parent, selected }"
                          >
                            <v-chip
                              v-if="item === Object(item)"
                              v-bind="attrs"
                              :color="`${item.color} lighten-3`"
                              :input-value="selected"
                              label
                              small
                            >
                              <span class="pr-2">
                                {{ item.text }}
                              </span>
                              <v-icon small @click="parent.selectItem(item)">
                                close
                              </v-icon>
                            </v-chip>
                          </template>
                        </v-combobox>
                      </v-card-text>
                    </v-card> </v-col
                  ><v-col cols="12">
                    <v-card color="#EDE7F6" height="100%">
                      <v-card-title> Descripción </v-card-title>
                      <v-card-text>
                        <v-textarea
                          v-model="empresa.descripcion"
                          :error-messages="validate.descripcion"
                          label=""
                          persistent-placeholder
                          outlined
                          clearable
                          rounded
                          required
                          hint="150 y 250 caracteres"
                          persistent-hint
                          prepend-icon="mdi-comment"
                          counter="250"
                          rows="2"
                          dense
                        ></v-textarea>
                      </v-card-text>
                    </v-card>
                  </v-col>
                </v-row>
              </v-col>
              <v-col cols="12" sm="6">
                <v-row>
                  <v-col cols="12">
                    <v-card color="#E0F2F1">
                      <v-card-title> Imágenes </v-card-title>
                      <v-card-text>
                        <v-row>
                          <v-col cols="12" sm="6">
                            <v-card class="mt-4" width="250">
                              <v-card-title> logo </v-card-title>
                              <v-divider class="mx-1"></v-divider>
                              <div class="image-upload mt-2">
                                <label for="file-logo">
                                  <img
                                    v-if="logo"
                                    :src="logo"
                                    alt=""
                                    class="preview"
                                  />
                                  <img
                                    v-else
                                    :src="empresa.logo"
                                    class="preview"
                                  />
                                </label>
                                <!-- <v-file-input
                                  v-model="uplogo"
                                  @change="onFileChange"
                                  id="file-input"
                                  hide-input
                                  label="Avatar"
                                  prepend-icon=""
                                ></v-file-input> -->
                                <input
                                  id="file-logo"
                                  type="file"
                                  accept="image/*"
                                  @change="onFileChange"
                                  name="images"
                                /><v-card-actions>
                                  <v-spacer></v-spacer>
                                  <v-btn icon @click="imglogo()">
                                    <v-icon dark right
                                      >mdi-content-save-outline</v-icon
                                    >
                                    Agregar </v-btn
                                  ><v-spacer></v-spacer>
                                </v-card-actions>
                              </div>
                            </v-card>
                          </v-col>
                          <v-col cols="12" sm="6"
                            ><v-card class="mt-4" width="250">
                              <v-card-title> Favicon </v-card-title>
                              <v-divider class="mx-1"></v-divider>
                              <div class="image-upload mt-2">
                                <label for="file-favi">
                                  <img
                                    v-if="Favi"
                                    :src="Favi"
                                    alt=""
                                    class="preview"
                                  />
                                  <img
                                    v-else
                                    :src="empresa.favicon"
                                    class="preview"
                                  />
                                </label>
                                <!-- <v-file-input
                                  v-model="upFavi"
                                  @change="onFileChangef"
                                  id="file-inputf"
                                  hide-input
                                  label="Avatar"
                                  prepend-icon=""
                                ></v-file-input> -->
                                <input
                                  id="file-favi"
                                  type="file"
                                  accept="image/*"
                                  @change="onFileChangef"
                                  name="imagesd"
                                />
                              </div>
                              <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn icon @click="imgfavi()">
                                  <v-icon dark right
                                    >mdi-content-save-outline</v-icon
                                  >
                                  Agregar </v-btn
                                ><v-spacer></v-spacer>
                              </v-card-actions>
                            </v-card>
                          </v-col>
                        </v-row>
                      </v-card-text>
                    </v-card>
                  </v-col>
                </v-row>
              </v-col>

              <v-col cols="12">
                <v-card color="#FFF3E0" height="100%">
                  <v-card-title> Footer </v-card-title>
                  <v-card-text>
                    <v-row
                      >
                      <v-col>
                        <v-text-field
                          v-model="footer.numero"
                          :error-messages="validate.titulo"
                          persistent-placeholder
                          outlined
                          clearable
                          rounded
                          required
                          hint="5 y 70 caracteres"
                          persistent-hint
                          label="Número"
                          dense
                        ></v-text-field>
                      </v-col>
                      <v-col>
                        <v-text-field
                          v-model="footer.direccion"
                          :error-messages="validate.titulo"
                          persistent-placeholder
                          outlined
                          clearable
                          rounded
                          required
                          hint="5 y 70 caracteres"
                          persistent-hint
                          label="Dirección"
                          dense
                        ></v-text-field>
                      </v-col>
                      <v-col>
                        <v-text-field
                          v-model="footer.correo"
                          :error-messages="validate.titulo"
                          persistent-placeholder
                          outlined
                          clearable
                          rounded
                          required
                          hint="5 y 70 caracteres"
                          persistent-hint
                          label="Correos"
                          dense
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-card>
              </v-col>
            </v-row>
            <div class="text-right mt-4">
              <v-btn color="primary" @click="e1 = 2"> Continue </v-btn>

              <v-btn text> Cancel </v-btn>
            </div>
          </v-stepper-content>

          <v-stepper-content step="2">
            <v-row>
              <v-col cols="12">
                <v-card color="#E0F2F1">
                  <v-card-title> Nosotros </v-card-title>
                  <v-card-text>
                    <v-textarea
                      v-model="empresa.nosotros"
                      :error-messages="validate.descripcion"
                      persistent-placeholder
                      outlined
                      clearable
                      rounded
                      required
                      hint="150 y 250 caracteres"
                      persistent-hint
                      prepend-icon="mdi-comment"
                      counter="250"
                    ></v-textarea> </v-card-text
                ></v-card>
              </v-col>
              <v-col cols="12">
                <v-card color="#E8EAF6">
                  <v-card-title> Misión </v-card-title>
                  <v-card-text>
                    <v-textarea
                      v-model="empresa.mision"
                      :error-messages="validate.descripcion"
                      persistent-placeholder
                      outlined
                      clearable
                      rounded
                      required
                      hint="150 y 250 caracteres"
                      persistent-hint
                      prepend-icon="mdi-comment"
                      counter="250"
                    ></v-textarea>
                  </v-card-text>
                </v-card>
              </v-col>
              <v-col cols="12">
                <v-card color="#E8F5E">
                  <v-card-title> Visión </v-card-title>
                  <v-card-text>
                    <v-textarea
                      v-model="empresa.vision"
                      :error-messages="validate.descripcion"
                      persistent-placeholder
                      outlined
                      clearable
                      rounded
                      required
                      hint="150 y 250 caracteres"
                      persistent-hint
                      prepend-icon="mdi-comment"
                      counter="250"
                    ></v-textarea
                  ></v-card-text>
                </v-card>
              </v-col>
            </v-row>

            <div class="text-right mt-4">
              <v-btn color="primary" @click="e1 = 3"> Continue </v-btn>

              <v-btn text> Cancel </v-btn>
            </div>
          </v-stepper-content>

          <v-stepper-content step="3">
            <v-row>
              <v-col cols="12">
                <v-card>
                  <v-card-title> Redes Sociales </v-card-title>
                  <v-card-text>
                    <v-row class="mt-8">
                      <v-col
                        v-for="(icon, index) in empresa.redes"
                        :key="icon.nombre"
                        cols="12"
                        sm="6"
                        md="6"
                      >
                        <v-text-field
                          :prepend-inner-icon="icon.icono"
                          v-model="empresa.redes[index].link"

                          outlined
                          :label="icon.nombre"
                          :color="icon.color"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-card>
              </v-col>
            </v-row>

            <div class="text-right mt-4">
              <v-btn color="primary" @click="save"> Guardar </v-btn>

              <v-btn text> Salir </v-btn>
            </div>
          </v-stepper-content>
        </v-stepper-items>
      </v-stepper>
    </v-card>

    <v-snackbar
      v-model="alert.active"
      :timeout="timeout"
      :color="alert.type"
      bottom
      right
      text
    >
      {{ alert.text }}

      <template v-slot:action="{ attrs }">
        <v-btn color="blue" text v-bind="attrs" @click="alert.active = false">
          Cerrar
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>
<script>
export default {
  layout: 'dashboard',
  name: 'empresa',

  beforeRouteEnter(to, from, next) {
    to.meta.title = 'Info Empresa'
    next()
  },
  data() {
    return {
      e1: 1,
      route: '/web/1',
      empresa: [],
      footer: {},
      validate: [],
      isBusy: false,
      items: [],
      activator: null,
      attach: null,
      colors: [
        'deep-purple',
        'green',
        'purple',
        'indigo',
        'cyan',
        'teal',
        'orange',
        'blue',
      ],
      editing: null,
      editingIndex: -1,
      nonce: 1,

      model: [],
      x: 0,
      search: null,
      y: 0,
      redes: {},
      network: [
        {
          nombre: 'Link Facebook',
          icono: 'mdi-facebook',
          color: '#3b5998',
          link: '',
        },
        {
          nombre: 'Link Twitter',
          icono: 'mdi-twitter',
          color: '#55acee',
          link: '',
        },
        {
          nombre: 'Link Instagram',
          icono: 'mdi-instagram',
          color: '#3b5998',
          link: '',
        },
        {
          nombre: 'Link Youtube',
          icono: 'mdi-youtube',
          color: '#bb0000',
          link: '',
        },
        {
          nombre: 'Número de WhatsApp',
          icono: 'mdi-whatsapp',
          color: '#4dc247',
          link: '',
        },
        {
          nombre: 'Nombre Página Facebook',
          icono: 'mdi-facebook-messenger',
          color: '#0078FF',
          link: '',
        },
      ],
      images: [],
      logo: null,
      uplogo: null,
      Favi: null,
      upFavi: null,
      loading: false,
      timeout: 2500,
      alert: {
        active: false,
        type: 'error',
        text: '',
      },
    }
  },
  watch: {
    model(val, prev) {
      if (val.length === prev.length) return

      this.model = val.map((v) => {
        if (typeof v === 'string') {
          v = {
            text: v,
            color: this.colors[this.nonce - 1],
          }

          this.items.push(v)

          this.nonce++
        }

        return v
      })
    },
  },
  mounted() {
    this.load()
  },

  methods: {
    async load() {
      this.isBusy = true
      try {
        let response = await this.crud('get', this.route)

        this.empresa = response.data.data
        this.model = this.empresa.etiquetas
        
        //this.footer = this.empresa.footer
        //console.log(this.empresa.redes, 'uno')
        this.isBusy = false
        if (this.empresa.redes === null) {
          this.empresa.redes = this.network
        }
        if (this.empresa.footer === null) {
          this.empresa.footer = this.footer
        } else {
          this.footer = this.empresa.footer
        }
        console.log(this.empresa.redes, 'dos')
      } catch (error) {
        this.alert.active = !this.alert.active
        this.alert.type = 'red'
        this.alert.text = error.response.data.detail
        this.isBusy = false
        if (error.response.status === 401) {
          this.$auth.logout()
        }
      }
    },
    newItem() {
      this.drawer = !this.drawer
      this.addSave = 'post'
    },
    async save() {
      this.loading = true

      const data = new FormData()
      data.append('_method', 'PUT')
      data.append('titulo', this.empresa.titulo)
      data.append('descripcion', this.empresa.descripcion)
      data.append('logo', this.uplogo)
      data.append('favicon', this.upFavi)
      data.append('redes', JSON.stringify(this.empresa.redes))
      data.append('nosotros', this.empresa.nosotros)
      data.append('mision', this.empresa.mision)
      data.append('vision', this.empresa.vision)
      data.append('footer', JSON.stringify(this.footer))
      data.append('etiquetas', JSON.stringify(this.model))
      console.log(data)
      try {
        let response = await this.crud('post', this.route, data)
        this.alert.active = true
        this.alert.type = 'success'
        this.alert.text = response.data.msg
        this.drawer = false
        this.loading = false
        this.item = {}
        this.load(1)
      } catch (error) {
        this.alert.active = true
        this.alert.text = '¡Oops! Tenemos Un Problema'
        this.alert.type = 'warning'
        this.warning = response.data.msg
        this.loading = false
      }
    },

    onFileChange(evt) {
      let imglogo = evt.target.files[0]
      console.log(imglogo, '1')
      this.uplogo = imglogo
      var reader = new FileReader()

      reader.onload = (e) => {
        this.logo = e.target.result
      }
      reader.readAsDataURL(imglogo)
      console.log(imglogo, '2', this.logo)
    },

    onFileChangef(evt) {
      let imglogo = evt.target.files[0]

      this.upFavi = imglogo
      var reader = new FileReader()

      reader.onload = (e) => {
        this.Favi = e.target.result
      }
      reader.readAsDataURL(imglogo)
    },
    imglogo() {
      document.getElementById('file-logo').click()
    },
    imgfavi() {
      document.getElementById('file-favi').click()
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
