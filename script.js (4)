const numberButtons = document.querySelectorAll('[data-number]')
const operatorButtons = document.querySelectorAll('[data-operator]')
const acButton = document.querySelector('[data-allClear]')
const deletebutton = document.querySelector('[data-delete]')
const equalButton = document.querySelector('[data-equal]')
const currentDisplay = document.querySelector('[data-current]')
const previousDisplay = document.querySelector('[data-previous]')

class Calculator {
  constructor(currentDisplay, previousDisplay) {
    this.currentDisplay = currentDisplay;
    this.previousDisplay = previousDisplay;
    this.clear();
  }
  clear() {
    this.currentOperand = '';
    this.previousOperand = '';
    this.operation = undefined;
  }
  delete() {
    this.currentOperand = this.currentOperand.toString().slice(0, -1);
  }
  chooseOperator(operation) {
    if (this.currentOperand == '') return
    if (this.previousOperand != '') {
      this.compute();
    }
    this.operation = operation;
    this.previousOperand = this.currentOperand;
    this.currentOperand = '';
  }
  compute() {
    let computation;
    const prev = parseFloat(this.previousOperand);
    const curr = parseFloat(this.currentOperand);

    if (isNaN(prev) || isNaN(curr)) return

    switch (this.operation) {
      case '+':
        computation = prev + curr;
        break;
      case '-':
        computation = prev - curr;
        break;
      case '×':
        computation = prev * curr;
        break;
      case '÷':
        computation = prev / curr;
        break;
      default:
        return
    }
    this.currentOperand = computation;
    this.previousOperand = '';
    this.operation = undefined;
  }
  appendNumber(number) {
    if (number === '.' && this.currentOperand.includes('.')) return;
    this.currentOperand = this.currentOperand.toString() + number;
  }
  updateDisplay() {
    this.currentDisplay.innerText = this.currentOperand;
    if (this.operation != null) {
      this.previousDisplay.innerText = `${this.previousOperand} ${this.operation}`;
    } else {
      this.previousDisplay.innerText = '';
    }
  }
}

const calculator = new Calculator(currentDisplay, previousDisplay);

function ac() {
  calculator.clear();
  calculator.updateDisplay();
}
acButton.addEventListener('touchend', ac)

function equal() {
  calculator.compute();
  calculator.updateDisplay();
}
equalButton.addEventListener('touchend', equal)

for (let i of numberButtons) {
  function number() {
    calculator.appendNumber(i.innerText);
    calculator.updateDisplay();
  }
  i.addEventListener('touchend', number)
}

for (let i of operatorButtons) {
  i.addEventListener('touchend', operator)

  function operator() {
    calculator.chooseOperator(i.innerText);
    calculator.updateDisplay();
  }
}

deletebutton.addEventListener('touchend', delet);

function delet() {
  calculator.delete();
  calculator.updateDisplay();
}