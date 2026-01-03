# ⚖️ Calculadora de IMC: Desafio de Lógica e Tipagem

Seja bem-vindo(a) ao meu repositório de estudos! 👋

Este projeto vai além de um simples cálculo de Índice de Massa Corpórea (IMC). 
Usei este exercício clássico para treinar **clean code**, controle de fluxo e, principalmente, **manipulação de tipos de dados** no JavaScript.

O objetivo foi transformar a lógica matemática em um código legível, robusto e preparado para evitar bugs futuros.

---

## 🧠 Decisões Técnicas & Aprendizados

Durante o desenvolvimento, tomei algumas decisões estratégicas para melhorar a qualidade do código. 
Aqui estão as principais:

### 1. `Number()` vs `.toFixed()` 🐱‍👤
Um dos maiores desafios de quem está começando (e até de quem já coda há tempos) é a **tipagem fraca** do JavaScript.
Eu queria que o resultado do IMC tivesse apenas duas casas decimais para ficar visualmente agradável, mas me deparei com um comportamento interessante:

```javascript
// O método .toFixed(2) retorna uma STRING!
const imcString = (peso / (altura * altura)).toFixed(2); // Retorna "25.95" (texto)

// Se eu deixasse assim, poderia gerar bugs silenciosos no futuro (ex: tentar somar esse valor e acabar concatenando texto). 
// Para resolver isso e manter a consistência dos dados, envolvi a operação no construtor Number():

// Solução robusta:
const imc = Number((peso / (altura * altura)).toFixed(2));
```
**Resultado:** Consegui limitar as casas decimais visualmente sem abrir mão da tipagem correta (`number`). Isso garante que meu código seja mais seguro e previsível.

### 2. Por que `switch` e não `if/else`? 🤔
A solução mais comum para verificar faixas de valores (como as categorias de peso da OMS) seria usar vários `if` e `else if` encadeados. Funciona? Sim. Mas tende a ficar verboso e visualmente poluído.

Para esse exercício, optei por uma abordagem mais limpa usando `switch(true)`:

```javascript
switch (true) {
  case imc < 17:
    console.log("Muito abaixo do peso");
    break;
  case imc >= 17 && imc <= 18.49:
    console.log("Abaixo do peso");
    break;
  // ... demais casos
}
```

**A vantagem dessa abordagem:**

* **Legibilidade:** Cada caso funciona como uma "regra" clara e isolada.
* **Manutenção:** É muito mais fácil bater o olho e entender os intervalos numéricos do que ler múltiplos blocos aninhados.
* **Estética:** O código fica mais organizado e elegante.

---
## 💡 Funcionalidades

* **Cálculo Preciso:** Baseado na fórmula oficial de IMC (Peso / Altura²).
* **Classificação Dinâmica:** Retorna resultados personalizados de acordo com a tabela da Organização Mundial da Saúde (OMS).
* **Tratamento Numérico:** Uso do método `.toFixed(2)` para garantir que o resultado seja amigável ao usuário, combinado com `Number()` para manter a tipagem correta.
* **Lógica Avançada de Comparação:** Implementação de `switch(true)` e operadores lógicos (`&&`) para validar intervalos de peso com precisão.

---

## 🚀 Conclusão
Este pequeno projeto reforçou para mim que programar não é apenas escrever linhas de código, mas tomar decisões. Escolher o tipo de dado correto e a estrutura de controle mais adequada faz toda a diferença entre um código que apenas roda e um código profissional.

Sigo estudando com garra e foco! 💻💜

---

## 📂 Outros Projetos em JavaScript

Explore outros desafios onde apliquei lógica e interatividade!

<br>
<div align="center">
    <a href="https://github.com/miriaamaral/JS-Jogo-Detona-Ralph" target="_blank" style="text-decoration: none;">
        <img src="https://github.com/miriaamaral/JS-Jogo-Detona-Ralph/raw/main/assets/img/thumb-detona-ralph.png" alt="Miniatura do Projeto Jogo Detona Ralph" width="300px" style="border-radius: 8px; margin: 10px;">
        <p style="color: #B18B77; font-weight: bold;">Jogo Detona Ralph</p>
    </a>
    <a href="https://github.com/miriaamaral/JS-Jogo-da-Memoria" target="_blank" style="text-decoration: none;">
        <img src="https://github.com/miriaamaral/JS-Jogo-da-Memoria/raw/main/assets/img/thumb-jogo-da-memoria.png" alt="Miniatura do Projeto Jogo da Memória" width="300px" style="border-radius: 8px; margin: 10px;">
        <p style="color: #B18B77; font-weight: bold;">Jogo da Memória JS</p>
    </a>
    <a href="https://github.com/miriaamaral/JS-Pokedex" target="_blank" style="text-decoration: none;">
        <img src="https://github.com/miriaamaral/JS-Pokedex/raw/main/assets/img/thumb-pokedex.png" alt="Miniatura do Projeto Pokedex JS" width="300px" style="border-radius: 8px; margin: 10px;">
        <p style="color: #B18B77; font-weight: bold;">Pokedex JS</p>
    </a>
</div>

---

## ⚙️ Como Rodar o Projeto (Localmente)

1. **Clone este repositório:**
   ```bash
   git clone https://github.com/miriaamaral/JS-calculadoraIMC.git
   ```

2. **Entre na pasta do projeto:**
   ```bash
   cd JS-calculadoraIMC
   ```

3. **Execute o arquivo via Terminal (com Node.js instalado):**
   ```bash
   node index.js
   ```
