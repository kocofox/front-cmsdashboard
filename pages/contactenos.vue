<template>
  <div>
    <v-container>
      <h1
        class="display-2 font-weight-bold mb-3 mt-8 text-uppercase text-center"
      >
        CONTÁCTENOS
      </h1>

      <v-responsive class="mx-auto mb-10" width="56">
        <v-divider class="mb-1"></v-divider>

        <v-divider></v-divider>
      </v-responsive>
      <h4 class="text-center mb-9">
        Muchas gracias por su interés en nuestra empresa y nuestros servicios,
        si tiene alguna pregunta, ¡escríbanos un mensaje ahora!!
      </h4>
      <v-row class="mt-8">
        <v-col cols="12" sm="4" >
          
                <v-responsive class="d-none d-sm-flex" >
                  <iframe
                    width="100%"
                    height="420"
                    frameborder="0"
                    scrolling="no"
                    marginheight="0"
                    marginwidth="0"
                    src="https://maps.google.com/maps?width=100%25&amp;height=600&amp;hl=es&amp;q=-12.060935,%20-77.016922+(Mi%20no%20ESB%20-%20NEGOCIOS%20Y%20PRODUCCI%C3%93N%20S.A.C.mbre%20de%20egocios)&amp;t=&amp;z=14&amp;ie=UTF8&amp;iwloc=B&amp;output=embed"
                  ></iframe
                  >
                </v-responsive>
              
        </v-col>
        <v-col cols="12" sm="8">
          <v-card flat  >
           
              <v-row dense>
                <v-col cols="12" sm="8">
                  <v-text-field
                  v-model="mensaje.razonSocial"
                  :error-messages="warning.razonSocial"
                    persistent-placeholder
                    outlined
                    required
                    persistent-hint
                    label="Razon Social / Nombres"
                    prepend-icon="mdi-card-account-details-outline"
                  ></v-text-field>
                </v-col>

                <v-col cols="12" sm="4">
                  <v-text-field
                  v-model="mensaje.ruc"
                  :error-messages="warning.ruc"
                    persistent-placeholder
                    outlined
                    required
                    persistent-hint
                    label="R.U.C / DNI"
                    prepend-icon="mdi-card-account-details-outline"
                  ></v-text-field>
                </v-col>

                <v-col cols="12" sm="6">
                  <v-text-field
                  v-model="mensaje.correo"
                  :error-messages="warning.correo"
                    persistent-placeholder
                    outlined
                    required
                    persistent-hint
                    label="CORREO"
                    prepend-icon="mdi-email-outline"
                  ></v-text-field>
                </v-col>

                <v-col cols="12" sm="6">
                  <v-text-field
                  v-model="mensaje.telefono"
                  :error-messages="warning.telefono"
                    persistent-placeholder
                    outlined
                    required
                    persistent-hint
                    label="TELÉFONO"
                    prepend-icon="mdi-phone-outline"
                  ></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-text-field
                  v-model="mensaje.asunto"
                  :error-messages="warning.asunto"
                    persistent-placeholder
                    outlined
                    required
                    persistent-hint
                    label="ASUNTO"
                    prepend-icon="mdi-comment-text-outline"
                  ></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-textarea
                  v-model="mensaje.mensaje"
                  :error-messages="warning.mensaje"
                    label="MENSAJE"
                    persistent-placeholder
                    outlined
                    required
                    hint="150 y 250 caracteres"
                    persistent-hint
                    prepend-icon="mdi-comment-text-multiple-outline"
                    counter="250"
                    rows="3"
                  ></v-textarea>
                </v-col>
                <v-col>
                  <div class="text-right mt-4 mb-8">
                    <v-btn outlined dark color="success" :loading="loading" @click="send()">
                      ENVIAR
                      <v-icon right> mdi-email-send-outline </v-icon></v-btn
                    >
                  </div>
                </v-col>
              </v-row>
           
          </v-card>
        </v-col>
      </v-row>
    </v-container>
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
  layout: 'homepage',
  data: () => ({
    mensaje: {},
    alert: {
        active: false,
        type: 'error',
        text: '',
      },
      loading: false,
      timeout: 2500,
      warning: {}

   
  }),

  methods: {
    async send() {
      this.loading = true
        let route =  "/contacto"
        let data = this.mensaje
      try {
        let response = await this.crud('post', route, data)
        this.alert.active = true
        this.alert.type = 'success'
        this.alert.text = response.data.msg
        
        this.item = {}
         this.loading = false
      } catch (error) {
       
        this.alert.active = true
        this.alert.text = error.response.data.message
        this.alert.type = 'warning'
       this.warning = error.response.data.errors
        this.loading = false
      }
    },
  },
}
</script>
