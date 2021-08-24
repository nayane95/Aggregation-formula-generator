<template>
  <div>
    <h1>Aggregation Formula Generator</h1>
    <!-- textArea  -->
    <v-textarea
      solo
      name="input-7-4"
      v-model="formula"
      ref="textarea"
      @click="cursorPosition()"
    ></v-textarea>
    <!-- InsertColumn Button  -->
    <v-btn block class="ma-2 ml-0" color="primary" @click="expand = !expand">
      Insert Column
    </v-btn>
    <!-- column name card -->
    <v-fab-transition>
      <v-card v-show="expand">
        <div>
          <v-select
            :items="dataSources"
            label="Data Source"
            item-text="schema"
            solo
            v-on:change="onDataSourceChange"
            v-model="schema"
          ></v-select>
          <v-select
            :items="columns"
            label="Column Name"
            v-model="column"
            solo
          ></v-select>
        </div>
        <v-btn color="primary" @click="setColumnName()">
          Insert
        </v-btn>
      </v-card>
    </v-fab-transition>
    <AggregateFunctions @clicked="insertTextToTextArea"/>
    <ArithmaticOperations @clicked="insertTextToTextArea"/>
    <LogicalOperators @clicked="insertTextToTextArea"/>

  </div>
</template>

<script>
export default {
  data: () => ({
    schema: null,
    column: null,
    dataSources: [
      { schema: "Customer", columns: ["id", "first_name", "last_name", "adress_line01", "adress_line02", "adress_line03", "age", "DOB"] },
      { schema: "Product", columns: ["id", "name", "price", "qty"] },
      { schema: "Employee", columns: ["id", "first_name", "last_name", "adress_line", "age", "DOB", "salary"] },
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
      if (cursorPos === undefined) {
        cursorPos = 0
      }
      this.formula =
        this.formula.substring(0, cursorPos) +
        text +
        this.formula.substring(cursorPos);

      // Get new cursor position
      cursorPos += text.length;

      // Wait until vue finishes rendering the new text and set the cursor position.
      this.$nextTick(() => textarea.setSelectionRange(cursorPos, cursorPos));
    },
    cursorPosition(){
      const textarea = this.$refs.textarea.$refs.input;

      // Insert text into current position
      let cursorPos = textarea.selectionEnd; // Get current Position
      console.log(cursorPos);
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
