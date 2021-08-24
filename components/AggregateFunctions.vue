<template>
    <v-card elevation="2">
      <!-- <AggregateFunctions /> -->
      <v-btn depressed color="error" @click="onClickButton(`SUM( )`)">
        SUM ( )
      </v-btn>
      <v-btn depressed color="error" @click="onClickButton(`COUNT( )`)">
        COUNT ( )
      </v-btn>
      <v-btn depressed color="error" @click="onClickButton(`AVG( )`)">
        AVG ( )
      </v-btn>
      <v-btn depressed color="error" @click="onClickButton(`MAX( )`)">
        MAX ( )
      </v-btn>
      <v-btn depressed color="error" @click="onClickButton(`MIN( )`)">
        MIN ( )
      </v-btn>
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
