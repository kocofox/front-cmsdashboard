<template>
  <section>
    <v-row no-gutters>
      <v-col cols="12">
        <v-container>
          <v-row class="py-16">
            <v-col cols="12">
              <h2
                class="
                  text-h4 text-md-h3 text-center
                  font-weight-black
                  text-capitalize
                "
              >
                ¿Quienes Somos?
              </h2>
              <h3
                class="text-h4 text-uppercase font-weight-thin text-center my-8"
              >
                ESB Es una empresa peruana que se desarrolla en el sector
                industrial dedicada a la Fabricación y montaje en estructuras
                metálicas
              </h3>
            </v-col>
            <v-col cols="12" >
              <p>
                Fabricación en estructuras y carpintería de aluminio con
                Cristales templados, crudos, Laminados, Montaje de Tabiquerías
                de Drywall y Superboard para campamentos mineros y ambientes de
                Oficina, Fabricación y montaje de estructuras de mimetizado en
                fibra de vidrio y Obras Civiles livianas para telecomunicación
              </p>

              <p>
                En ESB trabajamos con un grupo humano de experiencia en el
                sector para brindar nuevas ideas y soluciones necesarias que el
                cliente necesita para sus proyectos futuros y en ejecución,
                partiendo desde la planificación, ejecución y el seguimiento de
                los trabajos para dar como resultado productos y/o servicios de
                buena calidad.
              </p>
            </v-col>
          </v-row>
        </v-container>

        <v-row no-gutters>
          <v-col cols="12" md="6" align-self="center">
            <v-img
              max-height="800"
              src="qsomos/nosotros.jpg"
              lazy-src="qsomos/nosotros.jpg"
            >
            </v-img>
          </v-col>
          <v-col cols="12" md="6" align-self="center">
            <div class="pa-lg-16 pa-md-10 px-4 py-16">
              <h2 class="text-h3 text-center font-weight-black">MISIÓN</h2>
              <h3
                class="text-h6 text-uppercase font-weight-thin text-center my-8"
              >
               ESB Negocios & Producción SAC se compromete en brindar a sus clientes los servicios y productos de alta seguridad y calidad con los insumos y accesorios que trabaja, teniendo el objetivo de satisfacer las necesidades del cliente en un mercado de constante desarrollo.
              </h3>
             
            </div>
          </v-col>
        </v-row>
        <v-row no-gutters class="flex-row-reverse">
          <v-col cols="12" md="6" align-self="center">
            <v-img
              max-height="400"
              src="qsomos/mision_vision.jpg"
              lazy-src="qsomos/mision_vision.jpg"
            >
            </v-img>
          </v-col>
          <v-col cols="12" md="6" align-self="center">
            <div class="pa-lg-16 pa-md-10 px-4 py-16">
              <h2 class="text-h3 text-center font-weight-black">VISIÓN</h2>
              <h3
                class="text-h6 text-uppercase font-weight-thin text-center my-8"
              >
                Seguir creciendo en un mercado muy competitivo manteniendo la participación en los futuros proyectos del sector y ser reconocidos a nivel nacional.
              </h3>
              
            </div>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="12" md="6" align-self="center">
            <v-img
              max-height="800"
              src="qsomos/historia.jpg"
              lazy-src="qsomos/historia.jpg"
            >
            </v-img>
          </v-col>
          <v-col cols="12" md="6" align-self="center">
            <div class="pa-lg-16 pa-md-10 px-4 py-16">
              <h2 class="text-h3 text-center font-weight-black">HISTORIA</h2>
              <h3
                class="text-h6 text-uppercase font-weight-thin text-center my-8"
              >
              A mediados de 1989 iniciamos nuestras operaciones con el nombre de SERR-BA S.R.L. en la Fabricación de Espejos decorativos, Fabricación y Montaje de estructuras de Aluminio e instalación de Cristales para el mercado Inmobiliario.

Posteriormente para fines del año 2000 pasamos a ser EL PROGRESO, dejando a un lado la fabricación de espejos pero siguiendo con la misma área en Montaje de estructuras de Aluminio y Cristales agregando una nueva área de Fabricación y montaje de estructuras metálicas, y fue en Junio del 2010 cuando nace ESB NEGOCIOS Y PRODUCCION S.A.C. con el mismo equipo de colaboradores y la experiencia alcanzada por más 20 años en el rubro, ampliando su horizonte para desarrollar nuevos objetivos en un mundo globalizado que crece de manera vertiginosa. Hoy en día ESB se desempeña en diferentes actividades para colaborar con el desarrollo sostenible del País, teniendo la participación en Proyectos de Sub estaciones eléctricas, inmobiliarios y telecomunicaciones.
              </h3>
             
            </div>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  layout: 'homepage',
  data() {
    return {
      heroAlt: [
        {
          src: 'pexels-moose-photos-1036641.jpg',
          heading: ' About Us ',
        },
      ],
      ourTeam: [
        {
          name: 'John Churchill',
          position: 'Marketing Director',
          phone: '+1 (987) 1625346',
          email: 'john@example.com',
          photo: 'person-1.jpg',
        },
        {
          name: 'Fiona	Ross',
          position: 'Project Manager',
          phone: '+1 (987) 5894684',
          email: 'fiona@example.com',
          photo: 'person-2.jpg',
        },
        {
          name: 'Justin	Rees',
          position: 'VP Marketing',
          phone: '+1 (987) 6982456',
          email: 'justin@example.com',
          photo: 'person-3.jpg',
        },
        {
          name: 'Amelia	Ogden',
          position: 'Communication Manager',
          phone: '+1 (987) 6982456',
          email: 'amelia@example.com',
          photo: 'person-4.jpg',
        },
        {
          name: 'Sebastian Bailey',
          position: 'Advertising Director',
          phone: '+1 (987) 6982456',
          email: 'sebastian@example.com',
          photo: 'person-5.jpg',
        },
        {
          name: 'Eric Sutton',
          position: 'Advertising Executive',
          phone: '+1 (987) 6982456',
          email: 'audrey@example.com',
          photo: 'person-6.jpg',
        },
        {
          name: 'Xia Yen',
          position: 'Advertising Manager',
          phone: '+1 (987) 6982456',
          email: 'christian@example.com',
          photo: 'person-7.jpg',
        },
        {
          name: 'Bernadette	Springer',
          position: 'Employee Relations Manager',
          phone: '+1 (987) 6982456',
          email: 'bernadette@example.com',
          photo: 'person-8.jpg',
        },
        {
          name: 'Elizabeth Newman',
          position: 'Project Manager',
          phone: '+1 (987) 6982456',
          email: 'elizabeth@example.com',
          photo: 'person-9.jpg',
        },
      ],
    }
  },
  head() {
    return {
      title: 'About Us',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Infographic hypotheses influencer user experience Long madel ture gen-z paradigm shift client partner network product seilans solve management influencer analytics leverage virality. incubator seed round massmarket. buyer agile development growth hacking business-to-consumer ecosystem',
        },
      ],
    }
  },
}
</script>