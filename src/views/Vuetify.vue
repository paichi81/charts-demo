<template lang="pug">
  v-container(fluid).Vuetify
    v-row
      v-col(cols="12" md="8" ).d-flex.flex-wrap
        v-card.flex
          v-card-text
            h1 Sparkline
            v-sparkline(
              :value="value"
              :gradient="gradient"
              :smooth="radius || false"
              :padding="padding"
              :line-width="width"
              :stroke-linecap="lineCap"
              :gradient-direction="gradientDirection"
              :fill="fill"
              :type="type"
              :auto-line-width="autoLineWidth"
              auto-draw
            )

            v-sparkline(
              :value="value"
              :gradient="gradient"
              :smooth="radius || false"
              :padding="padding"
              :line-width="width"
              :stroke-linecap="lineCap"
              :gradient-direction="gradientDirection"
              :fill="fill"
              type="bar"
              :auto-line-width="autoLineWidth"
              auto-draw
            )

      v-col(cols="12" md="4" )
        v-switch(v-model="radius" label="radius")
        v-switch(v-model="fill" label="Fill" :disabled="type !== 'trend'")
        v-switch(v-model="autoLineWidth" label="Auto-line-width" )
</template>

<script>
  const gradients = [
      ['#222'],
      ['#42b3f4'],
      ['red', 'orange', 'yellow'],
      ['purple', 'violet'],
      ['#00c6ff', '#F0F', '#FF0'],
      ['#f72047', '#ffd200', '#1feaea'],
  ]
  export default {
    props: {

    },
    data() {
      return {
        width: 2,
        radius: 10,
        padding: 8,
        lineCap: 'round',
        gradient: gradients[5],
        value: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0],
        gradientDirection: 'top',
        gradients,
        fill: false,
        type: 'trend',
        autoLineWidth: false,
      }
    }
  }
</script>
