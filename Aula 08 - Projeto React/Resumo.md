# Aula 08 — Projeto React

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu  

---

# Objetivos da Aula

A oitava aula revisou os fundamentos do **JavaScript** (variáveis, tipos, operadores, estruturas de controle, funções, arrays, objetos e manipulação do DOM) e aprofundou os conceitos centrais do **React**: *JSX*, componentes, *props*, *Virtual DOM* e reconciliação, listas com *keys* e renderização condicional, culminando no desenvolvimento de um projeto React completo.

---

# Contexto da Disciplina

O JavaScript é a linguagem que dá vida às páginas Web, permitindo controlar praticamente todos os aspectos dinâmicos de uma interface: manipular o DOM, criar animações, consumir dados de servidores e construir aplicações modernas e responsivas.

O React se apoia nesses fundamentos para organizar interfaces em **componentes reutilizáveis**, permitindo que o desenvolvedor descreva *o resultado esperado* da tela em vez de manipular manualmente cada elemento do DOM.

---

# Revisão de JavaScript

### Formas de Inclusão
- **Interno:** Código escrito diretamente no `<body>` dentro da tag `<script>`;
- **Externo:** Arquivo `.js` vinculado via `<script src="...">` — **boa prática** em projetos maiores;
- **Eventos inline:** Atributos como `onclick` e `onblur` diretamente nas tags.

### Variáveis
JavaScript é **case sensitive** (`nome`, `Nome` e `NOME` são identificadores distintos) e não exige declaração no início do código.

| Palavra-chave | Escopo | Observação |
| :--- | :--- | :--- |
| `var` | Função | Se declarada fora de funções, torna-se global. |
| `let` | Bloco `{ }` | Uso mais restrito e previsível. |
| `const` | Bloco `{ }` | Valor não pode ser reatribuído. |

### Tipos de Dados
- `String` — `"Olá"`;
- `Number` — `10`, `3.14`;
- `Boolean` — `true`, `false`;
- `Undefined` — valor não definido;
- `Null` — ausência intencional de valor;
- `Object` — `{ nome: "Ana", idade: 20 }`;
- `Array` — `[10, 20, 30]`;
- `Symbol` — identificador único;
- `BigInt` — números inteiros muito grandes.

> `typeof` verifica o tipo de um valor.

---

# Operadores

| Categoria | Operadores |
| :--- | :--- |
| **Aritméticos** | `+` `-` `*` `/` `%` (resto) `**` (exponenciação) `++` `--` |
| **Comparação** | `==` (valor) `===` (valor e tipo) `!=` `!==` `>` `<` `>=` `<=` |
| **Lógicos** | `&&` (E) `\|\|` (OU) `!` (NÃO) |
| **Atribuição** | `=` `+=` `-=` `*=` `/=` `%=` |

---

# Estruturas de Controle

### Condicionais
O `if` avalia uma expressão e executa o bloco se ela for verdadeira; pode ser complementado por `else` e encadeado com `else if`.

```javascript
const nota = 8;
if (nota >= 9) {
  console.log("Excelente");
} else if (nota >= 7) {
  console.log("Aprovado");
} else {
  console.log("Reprovado");
}

// Operador ternário
const resultado = nota >= 7 ? "Aprovado" : "Reprovado";
```

### Repetições
- `for` — quando se sabe/controla a quantidade de repetições;
- `while` — repete enquanto a condição for verdadeira;
- `do...while` — executa pelo menos uma vez e depois verifica a condição;
- `break` — interrompe a repetição imediatamente;
- `continue` — pula a iteração atual e passa para a próxima.

---

# Funções, Arrays e Objetos

### Funções
Blocos de código que executam uma tarefa específica, recebem parâmetros e retornam valores com `return`.

```javascript
function somar(a, b) {
  return a + b;
}

const multiplicar = (a, b) => a * b; // Arrow function
```

### Arrays
Armazenam vários valores em uma única variável, acessados por **índice**.

```javascript
const notas = [7, 8, 5, 9, 10];
notas.forEach((nota, indice) => console.log(indice, nota));
const aprovados = notas.filter(nota => nota >= 7);
```

### Objetos
Agrupam **propriedades** (dados) e **métodos** (funções). A palavra `this` referencia o próprio objeto.

```javascript
const aluno = {
  nome: "Carlos",
  curso: "ADS",
  apresentar() {
    console.log(`Meu nome é ${this.nome}`);
  }
};
```

### Funções Úteis
- `console.log()` — mensagens no console (depuração);
- `alert()` / `prompt()` / `confirm()` — interação básica com o usuário;
- `document.getElementById()` / `querySelector()` — seleção de elementos;
- `.addEventListener()` — adiciona eventos (clique, scroll, input);
- `.innerHTML` / `.textContent` — alteram o conteúdo de elementos.

---

# DOM — Document Object Model

O **DOM** é a representação em árvore da estrutura de uma página, permitindo que o JavaScript consulte e altere seu conteúdo.

- **Seleção:** `getElementById()`, `querySelector()`, `querySelectorAll()`;
- **Modificação:** `textContent`, `value`, `classList`, `createElement()`, `appendChild()`.

```javascript
const botao = document.querySelector("#botao");
const texto = document.querySelector("#mensagem");

botao.addEventListener("click", () => {
  texto.textContent = "Olá! O conteúdo foi alterado.";
});
```

---

# JSX

O **JSX** é uma extensão de sintaxe para JavaScript que permite escrever estruturas semelhantes ao HTML dentro do código JS, descrevendo as interfaces dos componentes React.

```jsx
const nome = "João";
const saudacao = <h1>Olá, {nome}!</h1>;
const resultado = <p>Soma: {10 + 5}</p>;
```

### Diferenças entre JSX e HTML:
- Utiliza `className` em vez de `class`;
- Utiliza `htmlFor` em vez de `for`;
- Elementos sem conteúdo devem ser fechados (ex.: `<img />`);
- Componentes devem retornar **um elemento raiz** ou usar `Fragment`;
- Expressões JavaScript são inseridas entre chaves `{ }`;
- O JSX é transformado em JavaScript antes da execução.

---

# Componentes

**Componentes** são unidades independentes e reutilizáveis da interface. No React, normalmente são **funções JavaScript que retornam elementos React** (geralmente em JSX).

```jsx
function Cabecalho() {
  return <h1>Catálogo React</h1>;
}

function App() {
  return (
    <main>
      <Cabecalho />
      <p>Explore os principais conceitos.</p>
    </main>
  );
}
```

### Regras e Boas Práticas:
- O nome da função deve começar com **letra maiúscula**;
- Use `return` para definir o que será exibido;
- Utilize `<NomeDoComponente />` para renderizá-lo;
- Combine componentes menores para montar páginas completas.

### Árvore de Componentes:
```text
App
├── Cabecalho
├── BarraDePesquisa
├── ListaDeConceitos
│   ├── CardConceito
│   └── CardConceito
└── Rodape
```

---

# Props

**Props** (*properties*) são os dados recebidos por um componente, permitindo enviar informações do componente **pai** para o **filho** e reutilizar a mesma estrutura com conteúdos diferentes.

```jsx
function CardConceito({ titulo, descricao }) {
  return (
    <article>
      <h2>{titulo}</h2>
      <p>{descricao}</p>
    </article>
  );
}

<CardConceito titulo="JSX" descricao="Sintaxe para descrever interfaces." />
<CardConceito titulo="Props" descricao="Entradas recebidas por componentes." />
```

### Tipos de Valores em Props:
- **Strings:** textos entre aspas;
- **Números:** valores numéricos entre chaves;
- **Booleanos:** `true` ou `false`;
- **Arrays e objetos:** estruturas de dados;
- **Funções:** referências a funções;
- **Elementos React:** conteúdo renderizável.

> **Fluxo de dados:** unidirecional — o pai organiza e fornece as informações; o filho recebe e apresenta.

---

# Virtual DOM e Reconciliação

| DOM | Virtual DOM |
| :--- | :--- |
| Representa a estrutura do documento no navegador. | Modelo conceitual das descrições da interface em memória. |
| Pode ser consultado e modificado por JavaScript. | Utilizado pelo React para coordenar atualizações. |
| Reflete o documento renderizado. | Representa como a interface *deve* se apresentar. |

### Ciclo de Atualização da Interface:
1. **Mudança:** ocorre uma interação ou atualização de dados;
2. **Renderização:** o React executa novamente os componentes relevantes;
3. **Reconciliação:** compara a nova descrição com a anterior;
4. **Atualização:** aplica apenas as alterações necessárias ao DOM.

> O React usa o **tipo do elemento**, sua **posição na árvore** e as **keys** para identificar quais elementos representam a mesma parte lógica da interface.

---

# Listas e Keys

O método `map()` transforma cada item de um array em um elemento da interface, evitando escrever cada item manualmente. A propriedade especial **`key`** identifica elementos irmãos, ajudando o React a reconhecer itens mantidos, adicionados, removidos ou reordenados.

```jsx
const alunos = [
  { id: 1, nome: "Ana" },
  { id: 2, nome: "Bruno" },
  { id: 3, nome: "Caio" }
];

<ul>
  {alunos.map(aluno => <li key={aluno.id}>{aluno.nome}</li>)}
</ul>
```

### Combinando `filter()` e `map()`:
```jsx
const basicos = conceitos.filter(item => item !== "Hooks");
return <ul>{basicos.map(item => <li key={item}>{item}</li>)}</ul>;
```

> Use identificadores **estáveis** como key e, quando a lista estiver em estado, prefira produzir **novos arrays** em vez de modificar o existente.

---

# Renderização Condicional

Permite mostrar, ocultar ou alterar partes da interface conforme uma condição (props, estado ou dados recebidos).

### Com `if` e `return` (interfaces muito diferentes):
```jsx
function MensagemAcesso({ autenticado }) {
  if (!autenticado) {
    return <p>Entre para continuar.</p>;
  }
  return <p>Bem-vindo de volta!</p>;
}
```

### Com Operador Ternário (alternar mensagens):
```jsx
function ResultadoBusca({ carregando }) {
  return <p>{carregando ? "Buscando..." : "Busca finalizada."}</p>;
}
```

- Listas vazias podem exibir mensagens como *"Nenhum resultado encontrado."*;
- Estados de **carregamento**, **erro** e **sucesso** podem exigir tratamentos distintos.

---

# Atividade Prática da Aula

### Projeto React Completo
1. Desenvolver uma aplicação React utilizando **todos os conceitos estudados**: JSX, componentes, props, Virtual DOM, listas e renderização condicional;
2. Criar um **repositório público no GitHub**;
3. Documentar com um `README.md` contendo a descrição, as funcionalidades e os conceitos utilizados.

### Links Complementares:
- **Conceitos:** https://github.com/deivisontakatu/aula-react
- **Exemplo:** https://github.com/deivisontakatu/projeto-react
- **Aplicação:** https://projeto-react-ve-swart.vercel.app/
- **Material JS:** https://github.com/deivisontakatu/aula-javascript

---

# Principais Conceitos Aprendidos

- O JavaScript fornece a base (variáveis, funções, arrays, objetos e DOM) sobre a qual o React é construído.
- O JSX combina estrutura visual e expressões JavaScript em uma sintaxe próxima ao HTML.
- Componentes dividem a interface em partes menores, organizadas e reutilizáveis.
- Props permitem passar dados do componente pai para o filho em fluxo unidirecional.
- O Virtual DOM e a reconciliação permitem que o React aplique apenas as mudanças necessárias.
- `map()` com `key` renderiza listas de forma eficiente e previsível.
- A renderização condicional adapta a interface aos dados e ao estado da aplicação.

---

# Resumo Final

A oitava aula consolidou a ponte entre o JavaScript e o React. Após revisar os fundamentos da linguagem e a manipulação direta do DOM, foram apresentados os pilares do React: o JSX para descrever interfaces, os componentes para organizar e reutilizar partes da tela, as props para o fluxo de dados entre componentes, o Virtual DOM e a reconciliação para atualizações eficientes, além da renderização de listas com keys e da renderização condicional. A aula foi concluída com o desafio de construir um projeto React completo, publicado e documentado no GitHub.
