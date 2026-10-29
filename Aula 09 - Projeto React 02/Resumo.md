# Aula 09 — Projeto React 02

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu  

---

# Objetivos da Aula

A nona aula deu continuidade ao desenvolvimento com **React**, aprofundando o gerenciamento de estado com o Hook `useState`, a construção e validação de **Formulários** com campos controlados e `e.preventDefault()`, o uso do Hook `useEffect` para sincronização com efeitos externos e ciclo de vida (incluindo funções de limpeza), o **Consumo de APIs** assíncronas (requisições `GET` e `POST` com `fetch()`, tratamento de erros e boas práticas) e o roteamento de páginas em SPAs através do **React Router** (`react-router-dom`), consolidando os pilares necessários para criar aplicações web interativas e conectadas a serviços de dados.

---

# Contexto da Disciplina

Aplicações web modernas raramente se limitam a interfaces visuais estáticas. Elas precisam reagir às ações dos usuários em tempo real, recolher dados por meio de formulários interativos, sincronizar-se com serviços externos e APIs para obter ou persistir informações, e oferecer uma navegação rápida entre diferentes telas sem que o navegador recarregue a página inteira.

O ecossistema do React atende a essas demandas combinando o paradigma de **componentes funcionais** com **Hooks** nativos (`useState`, `useEffect`) e bibliotecas especializadas como o **React Router**. Dessa forma, o fluxo de desenvolvimento permanece declarativo, previsível, altamente modular e escalável.

---

# State e o Hook useState

O **state** (estado) representa qualquer dado ou informação interna que um componente armazena e que pode se transformar ao longo do tempo em resposta às interações do usuário, respostas de rede ou temporizadores.

### Por que uma Variável Comum não Basta?
Em JavaScript tradicional, poderíamos declarar uma variável local `let valor = 0`. No entanto, em componentes React:
1. Alterar uma variável comum **não avisa o React** que a interface precisa ser atualizada;
2. Quando o componente é renderizado novamente, todas as variáveis locais são **reinicializadas do zero**;
3. O **state** preserva os valores entre as renderizações e aciona o ciclo de re-renderização e reconciliação do Virtual DOM sempre que é modificado.

```jsx
// Exemplo do problema com variável comum:
function ContadorIncorreto() {
  let valor = 0;

  function incrementar() {
    valor = valor + 1; // A variável muda na memória, mas a tela não atualiza!
  }

  return <button onClick={incrementar}>Valor: {valor}</button>;
}
```

### O que são Hooks?
**Hooks** são funções especiais que permitem utilizar recursos de estado e ciclo de vida do React dentro de componentes funcionais.
- Seus nomes sempre iniciam com o prefixo `use` (ex.: `useState`, `useEffect`, `useParams`);
- **Regras dos Hooks:** devem ser chamados no nível superior do componente (nunca dentro de condicionais, repetições ou funções aninhadas).

### Sintaxe e Funcionamento do useState
O Hook `useState` deve ser importado do React e retorna um array com exatamente dois elementos:
1. **O valor atual do estado;**
2. **A função de atualização** responsável por alterar o valor e disparar uma nova renderização.

```jsx
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0); // 0 é o valor inicial

  return (
    <section>
      <p>Valor: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
    </section>
  );
}
```

---

# Formulários no React

Os formulários permitem a entrada de dados pelo usuário em cadastros, filtros de busca, autenticação e telas de preferências.

### Campos Controlados (Controlled Components)
No React, a boa prática padrão para formulários é utilizar **campos controlados**, onde o próprio estado do componente atua como a "única fonte da verdade" (*single source of truth*):
- O atributo `value` do `<input>` é vinculado a uma variável de estado;
- O evento `onChange` monitora a digitação do usuário e invoca a função de atualização com `e.target.value`.

```text
Digitação do Usuário ──▶ Evento onChange ──▶ setNome(e.target.value) ──▶ Atualização do Estado ──▶ Re-renderização com novo value
```

```jsx
import { useState } from "react";

function CampoNome() {
  const [nome, setNome] = useState("");

  return (
    <label>
      Nome:
      <input
        type="text"
        value={nome}
        onChange={(e) => setNome(e.target.value)}
        placeholder="Digite seu nome..."
      />
    </label>
  );
}
```

### Envio de Formulários e preventDefault()
Ao submeter um formulário HTML convencional, o navegador tenta executar seu comportamento padrão: enviar os dados para a URL do `action` e recarregar a página inteira.

Em aplicações React (SPAs), utilizamos o método **`e.preventDefault()`** dentro da função atrelada ao evento `onSubmit` da tag `<form>`:
- Evita o recarregamento indesejado da página;
- Mantém o estado da aplicação intacto;
- Permite validar dados, exibir feedbacks instantâneos ou enviar requisições assíncronas via `fetch()`.

```jsx
import { useState } from "react";

function FormularioUsuario() {
  const [email, setEmail] = useState("");

  function handleSubmit(e) {
    e.preventDefault(); // Impede o recarregamento padrão da página

    if (!email.includes("@")) {
      alert("Por favor, insira um e-mail válido.");
      return;
    }

    alert(`Cadastrado com sucesso: ${email}`);
    setEmail("");
  }

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Seu e-mail..."
      />
      <button type="submit">Enviar</button>
    </form>
  );
}
```

---

# O Hook useEffect e Sincronização

O **useEffect** é o Hook utilizado para executar **efeitos colaterais** (*side effects*), ou seja, ações que interagem com o mundo externo fora do fluxo direto de renderização da interface.

### Exemplos Típicos de Efeitos:
- Modificar elementos globais do navegador (como `document.title`);
- Configurar temporizadores (`setTimeout`, `setInterval`);
- Adicionar ou remover *listeners* de eventos globais (`window.addEventListener`);
- Realizar consultas e sincronização de dados com APIs remotas.

### O Array de Dependências
O segundo argumento passado ao `useEffect` é o array de dependências, que define **quando** o efeito deve ser executado:

| Array de Dependências | Comportamento de Execução | Caso de Uso |
| :--- | :--- | :--- |
| **Omitido** (`sem array`) | Executa após **toda e qualquer renderização**. | Raramente recomendado (risco de loops). |
| **Array Vazio** (`[]`) | Executa **apenas uma vez**, logo após o componente ser montado na tela. | Cargas iniciais de APIs, eventos globais de inicialização. |
| **Com Valores** (`[valor1, valor2]`) | Executa na montagem e **sempre que qualquer dependência mudar**. | Sincronização com props, buscas dinâmicas ao trocar filtros ou IDs. |

```jsx
// Exemplo: Atualizar o título da aba dinamicamente
import { useEffect } from "react";

function TituloPagina({ titulo }) {
  useEffect(() => {
    document.title = `${titulo} | Meu App`;
  }, [titulo]); // Executa novamente somente quando a prop "titulo" mudar

  return <h1>{titulo}</h1>;
}
```

### Limpeza de um Efeito (Cleanup Function)
Alguns efeitos alocam recursos que continuam consumindo memória se não forem devidamente finalizados (como *event listeners* ou *intervals*).
- A função de limpeza é retornada dentro do próprio `useEffect`;
- O React executa essa limpeza **antes de reexecutar o efeito** (caso as dependências mudem) e **quando o componente é desmontado** da interface (*unmount*).

```jsx
useEffect(() => {
  function handleResize() {
    console.log("Largura atual:", window.innerWidth);
  }

  window.addEventListener("resize", handleResize);

  // Função de limpeza essencial para evitar vazamento de memória:
  return () => {
    window.removeEventListener("resize", handleResize);
  };
}, []);
```

> **Regra de Ouro:** Tudo aquilo que for configurado em um efeito e puder permanecer ativo indevidamente deve ter uma limpeza correspondente retornada.

---

# Consumo de APIs com fetch()

Uma **API** (*Application Programming Interface*) permite a comunicação entre a aplicação React no cliente e servidores externos de backend para obter ou persistir dados.

### Buscando Dados com GET
No JavaScript moderno, utilizamos a função assíncrona **`fetch()`** em conjunto com `async/await`:
1. Dispara a requisição HTTP;
2. Avalia a propriedade `response.ok` para validar se a resposta retornou sucesso (status 200–299);
3. Converte os dados brutos para objeto JavaScript com `response.json()`.

```jsx
import { useEffect, useState } from "react";

function ListaPublicacoes() {
  const [publicacoes, setPublicacoes] = useState([]);
  const [carregando, setCarregando] = useState(true);
  const [erro, setErro] = useState(null);

  useEffect(() => {
    async function carregarDados() {
      try {
        const resposta = await fetch("https://jsonplaceholder.typicode.com/posts");
        if (!resposta.ok) {
          throw new Error(`Falha na requisição: status ${resposta.status}`);
        }
        const dados = await resposta.json();
        setPublicacoes(dados.slice(0, 5));
      } catch (err) {
        setErro(err.message);
      } finally {
        setCarregando(false);
      }
    }

    carregarDados();
  }, []); // Executa apenas na montagem

  if (carregando) return <p>Carregando publicações...</p>;
  if (erro) return <p>Erro: {erro}</p>;

  return (
    <ul>
      {publicacoes.map((item) => (
        <li key={item.id}>
          <strong>{item.title}</strong>
        </li>
      ))}
    </ul>
  );
}
```

### Enviando Dados com POST
Para persistir novas informações no servidor, passamos um objeto de opções como segundo argumento do `fetch()`:
- `method: "POST"`;
- `headers: { "Content-Type": "application/json" }` para informar o formato enviado;
- `body: JSON.stringify(objeto)` para serializar os dados no corpo da mensagem.

```jsx
async function cadastrarPublicacao(novoItem) {
  try {
    const resposta = await fetch("https://jsonplaceholder.typicode.com/posts", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(novoItem),
    });

    if (!resposta.ok) throw new Error("Erro ao salvar publicação.");

    const salvo = await resposta.json();
    console.log("Publicação salva com sucesso:", salvo);
  } catch (erro) {
    console.error(erro);
  }
}
```

### Cuidados e Boas Práticas ao Consumir APIs:
- **Tratamento de Exceções:** Sempre envolver chamadas assíncronas em blocos `try...catch` e verificar `response.ok`;
- **Estados de Interface:** Sempre contemplar carregamento (*loading*), erro (*error*), sucesso e estado vazio (*empty state*);
- **Evitar Loops Infinitos:** Garantir que dependências do `useEffect` estejam corretas e não alterar no efeito uma dependência que force sua execução contínua;
- **Segurança:** Nunca expor chaves de API secretas ou credenciais confidenciais no código do cliente;
- **Padrões de Rede:** Respeitar regras de CORS (*Cross-Origin Resource Sharing*), limites de requisições e autenticações.

---

# React Router — Navegação em SPAs

Em Single Page Applications (SPAs), a navegação entre telas não deve causar o recarregamento total do arquivo HTML. A biblioteca **React Router** (`react-router-dom`) associa caminhos da URL do navegador diretamente aos componentes visuais correspondentes.

### Componentes Fundamentais

| Componente | Função |
| :--- | :--- |
| `<BrowserRouter>` | Envolve toda a aplicação e monitora o histórico de navegação da URL no navegador. |
| `<Routes>` | Container que avalia as rotas filhas e renderiza a mais adequada para a URL atual. |
| `<Route path="..." element={<... />} />` | Mapeia um caminho específico (`path`) ao componente que deve ser exibido (`element`). |
| `<Link to="...">` | Renderiza links de navegação acessíveis que alteram a URL sem recarregar a página. |

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <header>
        <nav>
          <Link to="/">Início</Link>
          <Link to="/sobre">Sobre</Link>
          <Link to="/conceitos">Conceitos</Link>
        </nav>
      </header>

      <main>
        <Routes>
          <Route path="/" element={<Inicio />} />
          <Route path="/sobre" element={<Sobre />} />
          <Route path="/conceitos" element={<Conceitos />} />
          <Route path="/conceitos/:id" element={<DetalheConceito />} />
          <Route path="*" element={<NaoEncontrado />} />
        </Routes>
      </main>
    </BrowserRouter>
  );
}
```

### Parâmetros de Rota com useParams
Para exibir detalhes de um item específico (como um produto, usuário ou post), definimos caminhos com parâmetros variáveis usando dois-pontos (`:nomeDoParametro`). No componente de destino, lemos o valor através do Hook **`useParams()`**:

```jsx
import { useParams } from "react-router-dom";

function DetalheConceito() {
  const { id } = useParams(); // Obtém o parâmetro correspondente da URL

  return (
    <article>
      <h2>Visualizando Conceito</h2>
      <p>ID selecionado na URL: <strong>{id}</strong></p>
    </article>
  );
}
```

---

# Atividade Prática da Aula

### Desenvolvimento de Aplicação React Completa
1. Desenvolver uma aplicação React utilizando **todos os conceitos fundamentais estudados nesta aula**:
   - **State e useState:** Gerenciamento de estado interno e reatividade visual;
   - **Formulários:** Entradas controladas (`value` e `onChange`) e submissão com `e.preventDefault()`;
   - **useEffect:** Sincronização externa, chamadas assíncronas e limpezas quando necessário;
   - **Consumo de APIs:** Requisições assíncronas com `fetch()`, tratamento de erros e exibição de dados remotos;
   - **React Router:** Estrutura de navegação de páginas (`BrowserRouter`, `Routes`, `Route`, `Link` e rotas com `useParams`).
2. Criar um **repositório público no GitHub**;
3. Documentar a aplicação com um `README.md` abrangente, contendo descrição, funcionalidades implementadas e os conceitos de React aplicados.

### Links Complementares:
- **Conceitos:** https://github.com/deivisontakatu/aula-react
- **Exemplo:** https://github.com/deivisontakatu/projeto-react
- **Aplicação Demo:** https://projeto-react-five-swart.vercel.app/

---

# Principais Conceitos Aprendidos

- O `state` preserva dados entre renderizações e orienta o React sobre o momento exato de atualizar a interface na tela.
- Variáveis comuns em componentes funcionais são descartadas e recriadas a cada renderização, não notificando o ciclo de atualização do React.
- Hooks (`use...`) permitem acoplar estados e comportamentos a componentes funcionais seguindo regras rigorosas de escopo e ordem.
- Campos controlados tornam o estado do React a única fonte confiável de dados para formulários interativos.
- O `e.preventDefault()` é indispensável para evitar o recarregamento convencional de páginas e viabilizar a fluidez de uma SPA.
- O `useEffect` centraliza efeitos colaterais (APIs, títulos, timers e ouvintes de eventos) e seu array de dependências controla seu ciclo de execução.
- Funções de limpeza (*cleanup*) no `useEffect` garantem que ouvintes ou timers sejam cancelados, prevenindo vazamentos de memória.
- Requisições assíncronas com `fetch()`, `async/await`, validação de `response.ok` e `try...catch` estruturam o consumo resiliente de APIs.
- O React Router viabiliza rotas declarativas e navegação instantânea com `<Link>`, permitindo telas ricas com rotas parametrizadas via `useParams()`.

---

# Resumo Final

A nona aula consolidou o desenvolvimento de aplicações React interativas e integradas com serviços web. Foram explorados o gerenciamento de estado e reatividade com o Hook `useState`, o controle rigoroso de entradas e submissão de formulários, o ciclo de vida e efeitos colaterais com `useEffect` e suas funções de limpeza, bem como a comunicação assíncrona resiliente através do consumo de APIs via `fetch()`. Por fim, a introdução do React Router capacitou a estruturação de Single Page Applications completas com navegação dinâmica e parâmetros de URL, preparando os estudantes para o desenvolvimento do projeto prático solicitado.

