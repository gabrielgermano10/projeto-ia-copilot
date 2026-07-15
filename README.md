Projeto-IA/

├── package.json
├── README.md
├── src
│   ├── app.js
│   └── pedidos.js
├── tests
│   └── pedidos.test.js
└── .github
    └── workflows
        └── node.yml```json
{
  "name": "projeto-ia-copilot",
  "version": "1.0.0",
  "description": "Projeto utilizando GitHub Copilot e GitHub Actions",
  "main": "src/app.js",
  "scripts": {
    "start": "node src/app.js",
    "test": "jest"
  },
  "author": "Gabriel Germano",
  "license": "MIT",
  "devDependencies": {
    "jest": "^29.7.0"
  }
}
```javascript
/**
 * Gerado com o prompt utilizado no GitHub Copilot:
 *
 * "Crie uma função em JavaScript que calcule
 * o valor final de um pedido aplicando um
 * desconto percentual."
 */

function calcularTotal(valor, desconto) {
    return valor - (valor * desconto / 100);
}

module.exports = calcularTotal;
```
```javascript
const calcularTotal = require("./pedidos");

const total = calcularTotal(200, 10);

console.log("Valor final:", total);
```
```javascript
const calcularTotal = require("../src/pedidos");

test("Desconto de 10%", () => {
    expect(calcularTotal(100,10)).toBe(90);
});

test("Sem desconto", () => {
    expect(calcularTotal(100,0)).toBe(100);
});

test("Desconto de 50%", () => {
    expect(calcularTotal(200,50)).toBe(100);
});
```
```yaml
name: Node.js CI

on:
  push:
    branches:
      - main

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [20.x]

    steps:

      - uses: actions/checkout@v4

      - name: Instalar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}

      - name: Instalar dependências
        run: npm install

      - name: Executar testes
        run: npm test
```
