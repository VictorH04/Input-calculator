<template>
  <div class="calc">
    <div class="calc-space">
      <Plus1
        :Plus1="Plus.val1"
        v-model="Plus.val1"
        @getInput="getInput()"
        v-if="this.normal === true && this.Plus.check === true"
      />
      <Plus2
        :Plus2="Plus.val2"
        v-model="Plus.val2"
        @getInput="getInput()"
        v-if="this.normal === true && this.Plus.check === true"
      />

      <Minus1
        :Minus1="Minus.val1"
        v-model="Minus.val1"
        @getInput="getInput()"
        v-if="this.normal === true && this.Minus.check === true"
      />
      <Minus2
        :Minus2="Minus.val2"
        v-model="Minus.val2"
        @getInput="getInput()"
        v-if="this.normal === true && this.Minus.check === true"
      />

      <Division1
        :Division1="Division.val1"
        v-model="Division.val1"
        @getInput="getInput()"
        v-if="this.normal === true && this.Division.check === true"
      />

      <Division2
        :Division2="Division.val2"
        v-model="Division.val2"
        @getInput="getInput()"
        v-if="this.normal === true && this.Division.check === true"
      />

      <Multi1
        :Multi1="Multi.val1"
        v-model="Multi.val1"
        @getInput="getInput()"
        v-if="this.normal === true && this.Multi.check === true"
      />

      <Multi2
        :Multi2="Multi.val2"
        v-model="Multi.val2"
        @getInput="getInput()"
        v-if="this.normal === true && this.Multi.check === true"
      />

      <CalcSqRoot
        :calc3Value="ValueSqRoot"
        v-model="ValueSqRoot"
        @getInput="getInput()"
        v-if="this.SqRoot === true"
      />

      <CalcPercent
        :calc4Value="Percentage"
        v-model="Percentage"
        @getInput="getInput()"
        v-if="this.Percent === true"
      />

      <CalcPercent2
        :calc5Value="numPercentage"
        v-model="numPercentage"
        @getInput="getInput()"
        v-if="this.Percent === true"
      />

      <CalcSymbol :calcSymbol="this.calcSymbol" />
      <sumContainer :calcSum="calcSum" />
      <SelectVal
        @chooseCalculationPlus="checkCalc('Plus')"
        :Plus="this.calcList.Plus"
        @chooseCalculationMinus="checkCalc('Minus')"
        :Minus="this.calcList.Minus"
        @chooseCalculationDivision="checkCalc('Division')"
        :Division="this.calcList.Division"
        @chooseCalculationMultiplication="checkCalc('Multiplication')"
        :Multiplication="this.calcList.Multiplication"
        @chooseCalculationSquareRoot="checkCalc('SqRoot')"
        :SquareRoot="this.calcList.SquareRoot"
        @chooseCalculationPercent="checkCalc('Percent')"
        :Percent="this.calcList.Percent"
      />

      <ClearBtn @clearAll="clearAll()" />

      <CalcBtn @Calculate="Calculate()" />
    </div>
    <lastCalculations :answerArrays="this.arr" />

    <h1>{{ this.testing }}</h1>
  </div>
</template>

<script>
import Plus1 from "../components/inputs/Plus/PlusInput1.vue";
import Plus2 from "../components/inputs/Plus/PlusInput2.vue";

import Minus1 from "../components/inputs/Minus/MinusInput1.vue";
import Minus2 from "../components/inputs/Minus/MinusInput2.vue";

import Division1 from "../components/inputs/Division/DivisionInput1.vue";
import Division2 from "../components/inputs/Division/DivisionInput2.vue";

import Multi1 from "../components/inputs/Multi/MultiInput1.vue";
import Multi2 from "../components/inputs/Multi/MultiInput2.vue";

import CalcSqRoot from "../components/inputs/CalcSqRoot.vue";

import CalcPercent from "../components/inputs/CalcPercent.vue";
import CalcPercent2 from "../components/inputs/CalcPercent2.vue";

import sumContainer from "../components/Sum/SumContainer.vue";
import SelectVal from "../components/SelectCalc/SelectVal.vue";
import CalcSymbol from "../components/Symbol/calcSymbol.vue";
import ClearBtn from "../components/ClearBtn/ClearBtn.vue";
import CalcBtn from "../components/Calculate/Calculate.vue";

import lastCalculations from "../components/lastCalculations/lastCalculations.vue";

export default {
  name: "calcSpace",

  components: {
    Plus1,
    Plus2,

    Minus1,
    Minus2,

    Division1,
    Division2,

    Multi1,
    Multi2,

    sumContainer,
    SelectVal,
    CalcSymbol,
    ClearBtn,
    CalcBtn,
    CalcSqRoot,
    CalcPercent,
    CalcPercent2,

    lastCalculations,
  },

  data() {
    return {
      ValueSqRoot: null,
      Percentage: null,
      numPercentage: null,
      calcSum: "Please input a number",

      chosenCalc: 0,

      answer: null,
      totalAnswer: null,

      calcSymbol: "+",

      normal: true,
      SqRoot: false,
      Percent: false,

      calculation: "Plus",

      arr: [],

      count: 0,

      testing: null,

      Plus: {
        check: true,
        val1: null,
        val2: null,
      },

      Minus: {
        check: false,
        val1: null,
        val2: null,
      },

      Division: {
        check: false,
        val1: null,
        val2: null,
      },

      Multi: {
        check: false,
        val1: null,
        val2: null,
      },

      calcList: {
        Plus: "+",
        Minus: "-",
        Division: "/",
        Multiplication: "*",
        SquareRoot: "√",
        Percent: "%",
      },
    };
  },

  methods: {
    checkCalc(calc) {
      switch (calc) {
        case "Plus":
          this.Plus.check = true;
          this.Minus.check = false;
          this.Division.check = false;
          this.Multi.check = false;

          this.normal = true;
          this.Percent = false;
          this.SqRoot = false;

          this.calcSymbol = "+";

          console.log("Plus");
          this.clearAll();
          this.calculation = "Plus";
          break;

        case "Minus":
          this.Plus.check = false;
          this.Minus.check = true;
          this.Division.check = false;
          this.Multi.check = false;

          this.normal = true;
          this.Percent = false;
          this.SqRoot = false;

          this.calcSymbol = "-";

          console.log("Minus");
          this.clearAll();
          this.calculation = "Minus";
          break;

        case "Division":
          this.Plus.check = false;
          this.Minus.check = false;
          this.Division.check = true;
          this.Multi.check = false;

          this.normal = true;
          this.Percent = false;
          this.SqRoot = false;

          this.calcSymbol = "/";

          console.log("Division");
          this.clearAll();
          this.calculation = "Division";
          break;

        case "Multiplication":
          this.Plus.check = false;
          this.Minus.check = false;
          this.Division.check = false;
          this.Multi.check = true;

          this.normal = true;
          this.Percent = false;
          this.SqRoot = false;

          this.calcSymbol = "*";

          console.log("Multiplication");
          this.clearAll();
          this.calculation = "Multiplication";
          break;

        case "SqRoot":
          this.Plus.check = false;
          this.Minus.check = false;
          this.Division.check = false;
          this.Multi.check = false;

          this.normal = false;
          this.SqRoot = true;
          this.Percent = false;

          this.calcSymbol = "";

          console.log("SqRoot");
          this.clearAll();
          this.calculation = "SqRoot";
          break;

        case "Percent":
          this.Plus.check = false;
          this.Minus.check = false;
          this.Division.check = false;
          this.Multi.check = false;

          this.normal = false;
          this.SqRoot = false;
          this.Percent = true;

          this.calcSymbol = "";

          console.log("Percent");
          this.clearAll();
          this.calculation = "Percent";
          break;
      }

      // if (calc === "Plus") {
      //   this.Plus.check = tr ue;
      //   this.Minus.check = false;
      //   this.Division.check = false;
      //   this.Multi.check = false;

      //   this.normal = true;
      //   this.Percent = false;
      //   this.SqRoot = false;
      //   console.log("Plus");
      //   this.calculation = "Plus";

      // } else if (calc === "Minus") {
      //   this.Plus.check = false;
      //   this.Minus.check = true;
      //   this.Division.check = false;
      //   this.Multi.check = false;

      //   this.normal = true;
      //   this.Percent = false;
      //   this.SqRoot = false;
      //   console.log("Minus");
      //   this.calculation = "Minus";
      // } else if (calc === "Division") {
      //   console.log("Division");
      //   this.calculation = "Division";
      // } else if (calc === "Multiplication") {
      //   console.log("Multiplication");
      //   this.calculation = "Multiplication";
      // }
    },

    chooseCalculationPlus(num1, num2) {
      let Plus = parseInt(num1) + parseInt(num2);

      this.chosenCalc = `Is equal to: ${Plus}`;

      this.answer = Plus;

      this.calcSymbol = "+";
    },

    chooseCalculationMinus(num1, num2) {
      let Minus = parseInt(num1) - parseInt(num2);

      this.chosenCalc = `Is equal to: ${Minus}`;

      this.answer = Minus;

      this.calcSymbol = "-";

      console.log(this.chosenCalc);
    },

    chooseCalculationDivision(num1, num2) {
      let Divison = parseInt(num1) / parseInt(num2);

      this.chosenCalc = `Is equal to: ${Divison}`;

      this.answer = Divison;

      this.calcSymbol = "/";

      console.log(this.chosenCalc);
    },

    chooseCalculationMultiplication(num1, num2) {
      let Multi = parseInt(num1) * parseInt(num2);

      this.chosenCalc = `Is equal to: ${Multi}`;

      this.answer = Multi;

      this.calcSymbol = "*";

      console.log(this.chosenCalc);
    },

    chooseCalculationSquareRoot(num) {
      this.chosenCalc = Math.sqrt(num);

      this.answer = this.chosenCalc;

      this.calcSymbol = "";

      console.log(this.chosenCalc);
    },

    chooseCalculationPercent(num, percentage) {
      this.chosenCalc = num * (percentage / 100);

      this.answer = this.chosenCalc;

      this.calcSymbol = "";

      console.log(this.chosenCalc);
    },

    clearAll() {
      this.calcSum = "Please input a number";

      this.Plus.val1 = null;
      this.Plus.val2 = null;

      this.Minus.val1 = null;
      this.Minus.val2 = null;

      this.Division.val1 = null;
      this.Division.val2 = null;

      this.Multi.val1 = null;
      this.Multi.val2 = null;

      this.ValueSqRoot = null;
      this.Percentage = null;
      this.numPercentage = null;

      localStorage.removeItem("calculations");
    },

    clearSum() {
      this.calcSum = "Please input a number";
    },

    Calculate() {
      let foo = this.calculation;

      console.log(this.count);

      let oldData;

      switch (foo) {
        case "Plus":
          if (
            this.Plus.val1 &&
            this.Plus.val2 &&
            this.Minus.val1 &&
            this.Minus.val2 &&
            this.Division.val1 &&
            this.Division.val2 &&
            this.Multi.val1 &&
            this.Multi.val2 &&
            this.ValueSqRoot &&
            this.numPercentage &&
            this.Percentage === ""
          ) {
            console.log("Empty");
            alert("Please input a value");
          }

          this.chooseCalculationPlus(this.Plus.val1, this.Plus.val2);
          this.calcSum = this.chosenCalc;

          this.totalAnswer = `${this.Plus.val1} ${this.calcList.Plus} ${this.Plus.val2} = ${this.answer}`;

          if (localStorage.getItem("calculations") == null) {
            localStorage.setItem("calculations", "[]");
          }

          oldData = JSON.parse(localStorage.getItem("calculations"));

          if (oldData.length >= 5) {
            oldData.splice(5);
          }

          if (this.Plus.val1 && this.Plus.val2 && this.answer != null) {
            oldData.unshift([this.totalAnswer]);
          } else {
            // alert("Please input");
          }

          localStorage.setItem("calculations", JSON.stringify(oldData));

          this.arr.push(oldData[0].toString());
          this.arr.push(oldData[1].toString());
          this.arr.push(oldData[2].toString());
          this.arr.push(oldData[3].toString());
          this.arr.push(oldData[4].toString());

          console.log(oldData);
          break;

        case "Minus":
          this.chooseCalculationMinus(this.Minus.val1, this.Minus.val2);
          this.calcSum = this.chosenCalc;
          console.log(this.calcSum);
          console.log(this.chosenCalc);
          console.log(
            `${this.Minus.val1} ${this.calcList.Minus} ${this.Minus.val2} = ${this.answer}`
          );

          console.log(this.totalAnswer);
          console.log(this.arr);

          this.totalAnswer = `${this.Minus.val1} ${this.calcList.Minus} ${this.Minus.val2} = ${this.answer}`;

          console.log(this.arr);
          console.log(this.totalAnswer);
          break;

        case "Division":
          this.chooseCalculationDivision(
            this.Division.val1,
            this.Division.val2
          );
          this.calcSum = this.chosenCalc;
          console.log(this.calcSum);
          console.log(this.chosenCalc);
          console.log(
            `${this.Division.val1} ${this.calcList.Division} ${this.Division.val2} = ${this.answer}`
          );
          break;

        case "Multiplication":
          this.chooseCalculationMultiplication(
            this.Multi.val1,
            this.Multi.val2
          );
          this.calcSum = this.chosenCalc;
          console.log(this.calcSum);
          console.log(this.chosenCalc);
          console.log(
            `${this.Multi.val1} ${this.calcList.Multiplication} ${this.Multi.val2} = ${this.answer}`
          );
          break;

        case "SqRoot":
          this.chooseCalculationSquareRoot(this.ValueSqRoot);
          this.calcSum = this.chosenCalc;
          console.log(this.calcSum);
          console.log(this.chosenCalc);
          console.log(
            `${this.ValueSqRoot}${this.calcList.SquareRoot} = ${this.answer}`
          );
          break;

        case "Percent":
          this.chooseCalculationPercent(this.numPercentage, this.Percentage);
          this.calcSum = this.chosenCalc;
          console.log(this.calcSum);
          console.log(this.chosenCalc);
          console.log(
            `${this.Percentage}${this.calcList.Percent} of ${this.numPercentage} = ${this.answer}`
          );
          break;
      }
    },
  },

  mounted() {
    // this.chooseCalculationPlus();
    this.Calculate();
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
