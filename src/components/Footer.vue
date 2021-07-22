<template>
  <v-footer
    dark
    padless
  >
    <v-card
      class="flex"
      flat
      tile
    >
      <v-card-title class="color-footer">
        <v-layout>
            <v-flex>
                <v-btn icon href="" target="_blank" class="mx-15">
                    <h5>Término y condiciones</h5>
                </v-btn>

                <v-btn icon href="" target="_blank" class="ml-15 mr-7">
                    <h5>Privacidad</h5>
                </v-btn>

                <v-btn icon href="" target="_blank" class="mx-10">
                    <h5>Soporte</h5>
                </v-btn>
            </v-flex>
        </v-layout>

        <v-spacer></v-spacer>
        <a href="https://www.socialab.com/">Socialab.cl</a>
        
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4"
          dark
          icon
        >
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-title>
     
    </v-card>
  </v-footer>
</template>
<script>
  export default {
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
  }
</script>