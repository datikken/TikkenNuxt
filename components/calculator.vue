<template>
  <v-card class="calculator black--text">
    <div class="display">
      <div class="digit">
        {{ current || '0' }}
      </div>
    </div>
    <div class="btn" @click="clear">
      C
    </div>
    <div class="btn" @click="sign">
      +/-
    </div>
    <div class="btn" @click="percent">
      %
    </div>
    <div class="btn operator" @click="divide">
      ÷
    </div>
    <div class="btn" @click="append('7')">
      7
    </div>
    <div class="btn" @click="append('8')">
      8
    </div>
    <div class="btn" @click="append('9')">
      9
    </div>
    <div class="btn operator" @click="times">
      x
    </div>
    <div class="btn" @click="append('4')">
      4
    </div>
    <div class="btn" @click="append('5')">
      5
    </div>
    <div class="btn" @click="append('6')">
      6
    </div>
    <div class="btn operator" @click="minus">
      -
    </div>
    <div class="btn" @click="append('1')">
      1
    </div>
    <div class="btn" @click="append('2')">
      2
    </div>
    <div class="btn" @click="append('3')">
      3
    </div>
    <div class="btn operator" @click="plus">
      +
    </div>
    <div class="zero btn" @click="append('0')">
      0
    </div>
    <div class="btn" @click="dot()">
      .
    </div>
    <div class="btn operator" @click="equal">
      =
    </div>
  </v-card>
  </v-cardclass="white--text">
</template>

<script>
export default {
  data() {
    return {
      current: '',
      operator: null,
      previous: null,
      operatorClicked: false
    }
  },
  methods: {
    clear() {
      this.current = ''
    },
    sign() {
      this.current =
        this.current.charAt(0) === '-'
          ? this.current.slice(1)
          : `-${this.current}`
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = ''
        this.operatorClicked = false
      }
      this.current = `${this.current}${number}`
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.')
      }
    },
    divide() {
      this.operator = (a, b) => b / a
      this.setPrevious()
    },
    plus() {
      this.operator = (a, b) => a + b
      this.setPrevious()
    },
    times() {
      this.operator = (a, b) => a * b
      this.setPrevious()
    },
    minus() {
      this.setPrevious()
      this.operator = (a, b) => b - a
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`
      this.previous = null
    },
    setPrevious() {
      this.operatorClicked = true
      this.previous = this.current
    }
  }
}
</script>

<style scoped>
.calculator {
  width: 90vw;
  font-size: 30px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  display: grid;
  color: black;
  text-align: center;
  margin-top: 20px;
  float: right;
}

@media screen and (min-width: 450px) {
  .calculator {
    width: 400px;
  }
}
.display {
  grid-column: 1 / 5;
  background-color: #333;
  color: white;
  text-align: right;
}

.digit {
  margin-right: 41px;
}

@media screen and (max-width: 450px) {
  .digit {
    margin-right: 27px;
  }
}

.zero {
  grid-column: 1 / 3;
}

.btn {
  background-color: #f2f2f2;
  border: 1px solid #333;
}
.btn:hover {
  cursor: pointer;
}
.operator {
  background-color: orange;
  color: white;
}
</style>
