
# Aula 03 — Projetos com Frameworks Front-end

**Disciplina:** Frameworks Front-end
**Professor:** Prof. Me. Deivison S. Takatu

## 1. Introdução aos Frameworks Front-end

Um **framework Front-end** é um conjunto de ferramentas, bibliotecas e convenções que fornece uma estrutura para padronizar e acelerar o desenvolvimento de interfaces web.

Em comparação ao **Vanilla JavaScript**, frameworks permitem trabalhar com componentes reutilizáveis, gerenciamento de estado e atualizações mais eficientes da interface.

## 2. Framework × Biblioteca

A principal diferença está no controle do fluxo da aplicação:

| Framework                       | Biblioteca                                  |
| ------------------------------- | ------------------------------------------- |
| Controla o fluxo da aplicação | O desenvolvedor controla quando utilizá-la |
| Possui estrutura mais definida  | É mais flexível                           |
| Exemplos: Angular e Vue         | Exemplos: React e jQuery                    |

Essa diferença está relacionada ao conceito de **inversão de controle**, no qual o framework determina quando determinadas operações serão executadas.

> **Observação:** apesar de ser frequentemente chamado de framework, o React é tecnicamente uma biblioteca JavaScript para construção de interfaces.

## 3. Por que utilizar Frameworks?

Os frameworks oferecem diversos benefícios:

* Maior produtividade;
* Componentes e soluções reutilizáveis;
* Padronização do código;
* Manutenção facilitada;
* Recursos para gerenciamento de estado e rotas;
* Comunidades e documentação;
* Ferramentas e plugins;
* Otimizações de desempenho.

## 4. Características dos Frameworks

### Componentização

Os componentes encapsulam lógica e apresentação, podendo ser reutilizados em diferentes partes da aplicação. Isso facilita a manutenção e acelera o desenvolvimento.

### Programação Reativa

Frameworks como React, Vue e Angular permitem que a interface seja atualizada automaticamente quando o estado da aplicação é alterado, reduzindo a necessidade de manipulação manual do DOM.

### Build e Bundling

Ferramentas de build podem realizar tarefas como:

* Minificação;
* Transpilação;
* Combinação de arquivos;
* Otimização para navegadores.

### Rotas

Permitem criar **SPAs (Single Page Applications)** com navegação sem a necessidade de recarregar completamente a página.

### Integração com APIs

Os frameworks facilitam a comunicação assíncrona com serviços externos e o gerenciamento dos dados recebidos pelas APIs.

### Testes e Acessibilidade

Também podem oferecer ferramentas para testes unitários e de integração, além de componentes que seguem boas práticas de design e acessibilidade.

---

# 5. React

O **React**, desenvolvido pelo Facebook em 2013, é uma biblioteca JavaScript voltada para criação de interfaces de usuário dinâmicas e eficientes.

Sua arquitetura baseada em componentes e o uso do **Virtual DOM** permitem desenvolver aplicações reutilizáveis e escaláveis.

### Principais conceitos

#### Hooks

* `useState` → gerenciamento do estado de componentes funcionais;
* `useEffect` → gerenciamento de efeitos colaterais, como chamadas de API.

#### JSX

O JSX permite escrever uma estrutura semelhante ao HTML dentro do código JavaScript.

Características:

* Expressões JavaScript utilizam `{}`;
* Atributos seguem camelCase, como `className`;
* Tags precisam ser fechadas.

#### Gerenciamento de Estado

* **Context API:** adequada para estados menores;
* **Redux:** indicada para estados mais complexos e compartilhados globalmente.

### Virtual DOM

O React utiliza uma representação do DOM para identificar alterações e aplicar somente as diferenças necessárias no DOM real, buscando tornar as atualizações mais eficientes.

---

# 6. Angular

O **Angular** é um framework completo desenvolvido pelo Google, voltado principalmente para aplicações web, incluindo SPAs.

### Principais características

* TypeScript nativo;
* Roteamento;
* HTTP Client;
* Injeção de dependências;
* Arquitetura organizada;
* Angular CLI;
* Change Detection;
* Suporte à criação de componentes e serviços.

### Conceitos fundamentais

* **Componentes:** estrutura baseada em HTML, CSS e TypeScript;
* **Módulos:** organização da aplicação em blocos funcionais;
* **Serviços:** lógica reutilizável;
* **Data Binding:** comunicação entre dados e interface;
* **Injeção de Dependência:** gerenciamento de dependências;
* **Roteamento:** navegação entre diferentes views.

### Criando um projeto

```bash
npm install -g @angular/cli
ng new meu-app-angular
cd meu-app-angular
code .
ng serve
```

O **Angular CLI** é uma ferramenta de linha de comando utilizada para criar, gerenciar e construir projetos Angular.

---

# 7. Vue.js

O **Vue.js** é um framework progressivo baseado em componentes e programação reativa.

### Características

* Adoção gradual;
* Sistema de reatividade;
* Single-File Components (SFC);
* Curva de aprendizado acessível;
* Performance otimizada;
* Virtual DOM.

### Criando um projeto

```bash
npm create vue@latest
cd meu-projeto-vue
npm install
code .
npm run dev
```

### Estrutura

Entre os principais elementos estão:

* `src/` → código-fonte;
* `components/` → componentes reutilizáveis;
* `assets/` → imagens, fontes e CSS;
* `App.vue` → componente raiz;
* `main.js` → ponto de entrada;
* `vite.config.js` → configuração do Vite.

---

# 8. Next.js

O **Next.js** é um framework baseado em React para desenvolvimento de aplicações Web modernas e **full-stack**.

Ele adiciona recursos ao React, como:

* Roteamento baseado em arquivos;
* Renderização no servidor;
* Server Components;
* Otimização de imagens e fontes;
* Páginas e layouts;
* APIs e recursos de backend;
* Otimizações de desempenho e SEO.

### Criando um projeto

```bash
npx create-next-app@latest meu-projeto
cd meu-projeto
code .
npm run dev
```

## No **App Router**, a pasta `app/` organiza as páginas, layouts e rotas da aplicação. Arquivos `page.js` representam páginas e a estrutura das pastas determina as rotas.

# 9. Busca e Reutilização de Projetos

Não é necessário iniciar todos os projetos do zero. A comunidade **open source** disponibiliza diversos projetos que podem servir como base para novas aplicações.

Algumas fontes apresentadas na aula:

* GitHub;
* Vercel Templates;
* CodeSandbox.

No GitHub, por exemplo, é possível clonar um projeto utilizando:

```bash
git clone <url>
```

A utilização de projetos existentes pode acelerar o desenvolvimento e permitir a reutilização de soluções e boas práticas.

---

# 10. Atividade Prática

A atividade consiste em desenvolver **quatro projetos Web sobre o mesmo tema**, utilizando diferentes tecnologias:

1. **Projeto 01:** React;
2. **Projeto 02:** Vue;
3. **Projeto 03:** Angular;
4. **Projeto 04:** Next.js;
5. **Projeto 05:** cópia de um projeto obtido a partir de um repositório.

Cada aplicação deve possuir uma página funcional, responsiva e organizada, utilizando componentes e recursos básicos da tecnologia escolhida.

Os projetos deverão ser:

* Versionados com Git;
* Publicados no GitHub;
* Organizados em seus respectivos repositórios;
* Comparados entre si, destacando as diferenças encontradas durante o desenvolvimento.

---

# 11. Conclusão

A aula apresentou os principais conceitos de **Frameworks Front-end** e introduziu quatro tecnologias importantes:

| Tecnologia        | Caracterização apresentada                                       |
| ----------------- | ------------------------------------------------------------------ |
| **React**   | Biblioteca JavaScript para interfaces                              |
| **Angular** | Framework completo                                                 |
| **Vue**     | Framework progressivo                                              |
| **Next.js** | Framework baseado em React e voltado a aplicações Web/full-stack |

O principal objetivo prático foi compreender as diferenças entre essas tecnologias por meio do desenvolvimento de aplicações com o **mesmo tema**, permitindo comparar suas estruturas, ferramentas, componentes e formas de desenvolvimento.

**Conceitos principais:** Frameworks, bibliotecas, componentização, reatividade, Virtual DOM, TypeScript, JSX, rotas, APIs, Git, GitHub e estrutura de projetos.
