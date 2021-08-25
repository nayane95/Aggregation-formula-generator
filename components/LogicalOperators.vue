<template>
    <v-card elevation="3" class="mt-3">
      <!-- <Logical Operators /> -->
      <v-row class="mt-2">
        <v-col class="d-flex justify-center">
          <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` AND `)">
            <small>AND</small>
          </v-btn>
        </v-col>
        <v-col class="d-flex justify-center">
          <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` OR `)">
            <small>OR</small>
          </v-btn>
        </v-col>
        <v-col class="d-flex justify-center">
          <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` NOT `)">
            <small>NOT</small>
          </v-btn>
        </v-col>
        <v-col class="d-flex justify-center">
          <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` && `)">
            <small>&&</small>
          </v-btn>
        </v-col>
        <v-col class="d-flex justify-center">
          <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` || `)">
            <small>||</small>
          </v-btn>
        </v-col>
        <v-col class="d-flex justify-center">
          <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` > `)">
          >
          </v-btn>
        </v-col>
        <v-col class="d-flex justify-center">
           <v-btn class="mx-2" fab dark color="#4f4f4f" small @click="onClickButton(` < `)">
          <
          </v-btn>
        </v-col>
      </v-row>
    </v-card>
</template>

<script>
export default {
  data: () => ({

  }),
  methods: {
    onClickButton (textToSet) {
      this.$emit('clicked', textToSet);
    }
  }
};
</script>

<style>
.VuetifyLogo {
  height: 180px;
  width: 180px;
  transform: rotateY(560deg);
  animation: turn 3.5s ease-out forwards 1s;
}

@keyframes turn {
  100% {
    transform: rotateY(0deg);
  }
}

.neumorphism01 {
  border-radius: 50px;
  background: #4f4f4f;
  box-shadow: inset 22px 22px 30px #3d3d3d, inset -22px -22px 30px #616161;
}
</style>
