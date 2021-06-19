<template>
  <v-navigation-drawer
    app
    permanent
    :expand-on-hover="drawer"
    :mini-variant="drawer"
    class="menu-navigation-drawer"
    
  > 
    <v-list>
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src=""></v-img>
        </v-list-item-avatar>
        <v-list-item-title class="title text-h4">
          ESB NEg
        </v-list-item-title>
      </v-list-item>
      <v-list-item
        v-for="(item, i) in items"
        :key="i"
        :to="item.to"
        router
        exact
      >
        <v-list-item-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title v-text="item.title" />
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
<script>
export default {
 
  data() {
    return {
      items: [],
    }
  },
  computed: {
    drawer: {
      get() {
        return this.$store.state.drawer
      },
      set(val) {
        this.$store.commit('drawer', val)
      },
    },
  },
  mounted() {
    this.Menu()
  },
  methods: {
    Menu() {
      let user = this.$auth.user.profiles_id
      
      switch (user) {
        case 1:
          console.log('admin')
          return (this.items = [
            
            //superadmin
            {
              icon: 'mdi-briefcase-outline',
              title: 'EMPRESA',
              to: '/admin/empresa',
            },

            {
              icon: 'mdi-tooltip-image-outline',
              title: 'BANNERS',
              to: '/admin/banner',
            },
            {
              icon: 'mdi-tooltip-image-outline',
              title: 'CATEGORIAS',
              to: '/admin/categorias',
            },
            {
              icon: 'mdi-newspaper-variant-multiple-outline',
              title: 'NOTICIAS',
              to: '/admin/noticias',
            },
            {
              icon: 'mdi-account-group-outline',
              title: 'SERVICIOS',
              to: '/admin/servicios',
            },
            {
              icon: 'mdi-account-network-outline',
              title: 'CLIENTES',
              to: '/admin/clientes',
            },
            {
              icon: 'mdi-account-plus-outline',
              title: 'ROLES',
              to: '/admin/roles',
            },
            {
              icon: 'mdi-account-plus-outline',
              title: 'USUARIOS',
              to: '/admin/usuarios',
            },
            {
              icon: ' mdi-email-outline',
              title: 'MENSAJES',
              to: '/admin/mensajes',
            },
            
            
          ])
          break
        case '2':
          return (this.items = [
            // Administrador – Sutran y sub usuario

            // {
            //   icon: "mdi-card-account-details-outline",
            //   title: "TRANSPORTISTAS",
            //   to: "transportistas",
            // },
            {
              icon: 'mdi-account-multiple-plus-outline',
              title: 'USUARIOS TRANSPORTISTA',
              to: 'usertransportista',
            },
            {
              icon: 'mdi-rv-truck',
              title: 'VEHICULOS',
              to: 'vehiculos',
            },
            // {
            //   icon: " mdi-routes-clock",
            //   title: "RUTAS",
            //   to: "rutas",
            // },
            // {
            //   icon: "mdi-google-maps",
            //   title: "PUNTOS DE CONTROL",
            //   to: "puntoscontrol",
            // },
            // {
            //   icon: "mdi-alert-circle-outline",
            //   title: "Incidencias (SUTRAN)",
            //   to: "incidenciasmonitoreo",
            // },
            {
              icon: 'mdi-alert-circle-outline',
              title: 'Incidencias (TRANSPORTISTAS)',
              to: 'incidenciastransportistas',
            },
          ])
          break
        case 'productos':
          return '/' + this.name
          break
        case 'articulo':
          return '/' + this.name
          break
      }
    },
    selector() {
      let user = this.$auth.user
      // console.log(user);

      this.items = [
        //superadmin
        {
          icon: 'mdi-account-tie',
          title: 'USUARIOS SUTRAN',
          to: 'usersutran',
        },

        // Administrador – Sutran y sub usuario
        {
          icon: 'mdi-account-multiple-plus-outline',
          title: 'USUARIOS TRANSPORTISTA',
          to: 'usertransportista',
        },
        {
          icon: 'mdi-card-account-details-outline',
          title: 'TRANSPORTISTAS',
          to: 'transportistas',
        },
        {
          icon: 'mdi-rv-truck',
          title: 'VEHICULOS',
          to: 'vehiculos',
        },
        {
          icon: ' mdi-routes-clock',
          title: 'RUTAS',
          to: 'rutas',
        },
        {
          icon: 'mdi-google-maps',
          title: 'PUNTOS DE CONTROL',
          to: 'puntoscontrol',
        },
        {
          icon: 'mdi-alert-circle-outline',
          title: 'Incidencias (SUTRAN)',
          to: 'incidenciasmonitoreo',
        },
        {
          icon: 'mdi-alert-circle-outline',
          title: 'Incidencias (TRANSPORTISTAS)',
          to: 'incidenciastransportistas',
        },

        // {
        //   icon: "mdi-map-marker-multiple",
        //   title: "Rubros de Stand",
        //   to: "/rubrostands"
        // },

        // {
        //   icon: "mdi-text-box-outline",
        //   title: "Facturación",
        //   to: "/admin/voucher"
        // },
        // {
        //   icon: "mdi-brightness-7",
        //   title: "Administracion",
        //   to: "/user/administration"
        // }

        {
          icon: 'mdi-cart',
          title: 'Productos',
          to: '/admin/products',
          items: [],
        },
        {
          icon: 'mdi-clipboard-account-outline',
          title: 'Cuenta',
          to: '/admin/user',
          items: [],
        },
        // {
        //   icon: "mdi-apps",
        //   title: "Categorias",
        //   to: "/categories"
        // }
      ]
    },
  },
}
</script>
<style scoped>
.menu-navigation-drawer {
  z-index: 9999;
}
</style>