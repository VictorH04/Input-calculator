<template>
  <div class="calcSpace">
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
      @chooseCalculationPlus="chooseCalculationPlus(Plus.val1, Plus.val2)"
      :Plus="this.calcList.Plus"
      @chooseCalculationMinus="chooseCalculationMinus(Minus.val1, Minus.val2)"
      :Minus="this.calcList.Minus"
      @chooseCalculationDivision="
        chooseCalculationDivision(Division.val1, Division.val2)
      "
      :Division="this.calcList.Division"
      @chooseCalculationMultiplication="
        chooseCalculationMultiplication(Multi.val1, Multi.val2)
      "
      :Multiplication="this.calcList.Multiplication"
      @chooseCalculationSquareRoot="chooseCalculationSquareRoot(ValueSqRoot)"
      :SquareRoot="this.calcList.SquareRoot"
      @chooseCalculationPercent="
        chooseCalculationPercent(numPercentage, Percentage)
      "
      :Percent="this.calcList.Percent"
    />

    <CalcBtn @Calculate="Calculate()" />

    <ClearBtn @clearAll="clearAll()" />
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
  },

  data() {
    return {
      ValueSqRoot: null,
      Percentage: null,
      numPercentage: null,
      calcSum: "Please input a number",

      chosenCalc: 0,
      answer: null,

      calcSymbol: "+",

      normal: true,
      SqRoot: false,
      Percent: false,

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
    chooseCalculationPlus(num1, num2) {
      this.Plus.check = true;
      this.Minus.check = false;
      this.Division.check = false;
      this.Multi.check = false;

      this.clearAll();
      this.normal = true;
      this.Percent = false;
      this.SqRoot = false;

      let Plus = parseInt(num1) + parseInt(num2);

      this.chosenCalc = `Is equal to: ${Plus}`;

      this.calcSymbol = "+";

      console.log(this.chosenCalc);
    },

    chooseCalculationMinus(num1, num2) {
      this.Plus.check = false;
      this.Minus.check = true;
      this.Division.check = false;
      this.Multi.check = false;
      this.clearAll();

      this.normal = true;
      this.Percent = false;
      this.SqRoot = false;

      let Minus = parseInt(num1) - parseInt(num2);

      this.chosenCalc = `Is equal to: ${Minus}`;

      this.calcSymbol = "-";

      console.log(this.chosenCalc);
    },

    chooseCalculationDivision(num1, num2) {
      this.Plus.check = false;
      this.Minus.check = false;
      this.Division.check = true;
      this.Multi.check = false;
      this.clearAll();

      this.normal = true;
      this.Percent = false;
      this.SqRoot = false;

      let Divison = parseInt(num1) / parseInt(num2);

      this.chosenCalc = `Is equal to: ${Divison}`;

      this.calcSymbol = "/";

      console.log(this.chosenCalc);
    },

    chooseCalculationMultiplication(num1, num2) {
      this.Plus.check = false;
      this.Minus.check = false;
      this.Division.check = false;
      this.Multi.check = true;
      this.clearAll();

      this.normal = true;
      this.Percent = false;
      this.SqRoot = false;

      let Multi = parseInt(num1) * parseInt(num2);

      this.chosenCalc = `Is equal to: ${Multi}`;

      this.calcSymbol = "*";

      console.log(this.chosenCalc);
    },

    chooseCalculationSquareRoot(num) {
      this.clearAll();

      this.normal = false;
      this.SqRoot = true;
      this.Percent = false;
      this.chosenCalc = Math.sqrt(num);
      this.calcSymbol = "";

      console.log(this.chosenCalc);
    },

    chooseCalculationPercent(num, percentage) {
      this.clearAll();

      this.normal = false;
      this.SqRoot = false;
      this.Percent = true;
      this.chosenCalc = num * (percentage / 100);
      this.calcSymbol = "";

      console.log(this.chosenCalc);
    },

    clearAll() {
      if (this.Plus.check === true) {
        this.Minus.val1 = "";
        this.Minus.val2 = "";
        this.Division.val1 = "";
        this.Division.val2 = "";
        this.Multi.val1 = "";
        this.Multi.val2 = "";
        this.calcSum = "Please input a number";
      } else if (this.Minus.check === true) {
        this.Plus.val1 = "";
        this.Plus.val2 = "";
        this.Division.val1 = "";
        this.Division.val2 = "";
        this.Multi.val1 = "";
        this.Multi.val2 = "";
        this.calcSum = "Please input a number";
      } else if (this.Division.check === true) {
        this.Plus.val1 = "";
        this.Plus.val2 = "";
        this.Minus.val1 = "";
        this.Minus.val2 = "";
        this.Multi.val1 = "";
        this.Multi.val2 = "";
        this.calcSum = "Please input a number";
      } else if (this.Multi.check === true) {
        this.Plus.val1 = "";
        this.Plus.val2 = "";
        this.Minus.val1 = "";
        this.Minus.val2 = "";
        this.Division.val1 = "";
        this.Division.val2 = "";
        this.calcSum = "Please input a number";
      }
    },

    Calculate() {
      this.calcSum = this.chosenCalc;
    },
  },
};
</script>

<style lang="scss">
@import "SASS/base/_Home.scss";
</style>
