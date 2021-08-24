<template>
  <div>
    <v-btn
      class="mx-2"
      fab
      dark
      small
      color="pink"
    >
      <v-icon dark>
        mdi-heart
      </v-icon>
    </v-btn>
  </div>
</template>

<script>
export default {
  data: () => ({
    schema: null,
    column: null,
    dataSources: [
      { schema: "1111", columns: ["test1", "test2"] },
      { schema: "2222", columns: ["test4", "test3"] },
      { schema: "3333", columns: ["test5", "test6"] }
    ],
    columns: [],
    expand: false,
    formula: ""
  }),
  methods: {
    onDataSourceChange() {
      if (this.schema) {
        this.dataSources.forEach(element => {
          if (element.schema == this.schema) {
            this.columns = element.columns;
          }
        });
      }
    },
    setColumnName() {
      let text = `("` + this.schema + `.` + this.column + `") `;
      this.insertTextToTextArea(text);
      this.expand = !this.expand;
      this.reset();
    },
    insertTextToTextArea(text) {
      const textarea = this.$refs.textarea.$refs.input;

      // Insert text into current position
      let cursorPos = textarea.selectionEnd; // Get current Position
      this.formula =
        this.formula.substring(0, cursorPos) +
        text +
        this.formula.substring(cursorPos);

      // Get new cursor position
      cursorPos += text.length;

      // Wait until vue finishes rendering the new text and set the cursor position.
      this.$nextTick(() => textarea.setSelectionRange(cursorPos, cursorPos));
    },
    reset() {
      this.schema = null;
      this.column = null;
      this.columns = [];
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
