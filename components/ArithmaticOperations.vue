<template>
    <v-card elevation="3" class="mt-3">
      <!-- <Aritmatic operations /> -->
      <v-row class="mt-2">
        <v-col>
          <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` + `)">
            <v-icon dark>
              mdi-plus
            </v-icon>
          </v-btn>
        </v-col>
        <v-col>
          <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` - `)">
            <v-icon dark>
              mdi-minus
            </v-icon>
          </v-btn>
        </v-col>
        <v-col>
          <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` / `)">
            <v-icon dark>
              mdi-slash-forward
            </v-icon>
          </v-btn>
        </v-col>
        <v-col>
          <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` * `)">
            <v-icon dark>
              mdi-close
            </v-icon>
          </v-btn>
        </v-col>
        <v-col>
          <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` % `)">
            <v-icon dark>
              mdi-percent
            </v-icon>
          </v-btn>
        </v-col>
        <v-col>
          <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` ( `)">
          (
          </v-btn>
        </v-col>
        <v-col>
           <v-btn class="mx-2" fab dark color="indigo" small @click="onClickButton(` ) `)">
            )
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
