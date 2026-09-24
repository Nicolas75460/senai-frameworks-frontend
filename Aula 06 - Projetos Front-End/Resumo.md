# Aula 06 — Projetos Front-End

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu  

---

# Objetivos da Aula

A sexta aula teve como objetivo apresentar os conceitos e práticas essenciais para a gestão de projetos no desenvolvimento Front-End, abordando a relevância da organização do fluxo de trabalho, gestão de requisitos (da ideia às tarefas técnicas), estruturação do Backlog do produto, técnicas de priorização e estimativa, o conceito de *Definition of Done* (DoD) e a aplicação do framework ágil **Scrum** em projetos web.

---

# Contexto da Disciplina

À medida que os projetos de Front-End evoluem, a complexidade das interfaces, a quantidade de componentes e o volume de integrações com o back-end aumentam significativamente. 

Desenvolver sem um processo estruturado resulta frequentemente em desorganização e atrasos. Portanto, aprender a gerenciar um projeto Front-End — organizando pessoas, tarefas, tecnologias e prazos — é fundamental para transformar uma ideia inicial em uma aplicação robusta, funcional e alinhada às exigências do mercado.

---

# Por que Gerenciar um Projeto Front-End?

Sem um planejamento e acompanhamento adequados, projetos de desenvolvimento web enfrentam gargalos recorrentes que comprometem a qualidade e os prazos.

### Impactos da Ausência vs. Presença de Gestão

| Projetos Sem Gestão | Projetos Com Gestão |
| :--- | :--- |
| ❌ Tarefas esquecidas | ✅ Responsabilidades claras |
| ❌ Requisitos confusos e omissos | ✅ Prioridades bem definidas |
| ❌ Retrabalho constante | ✅ Entregas incrementais e funcionais |
| ❌ Conflitos de versionamento no Git | ✅ Acompanhamento contínuo do progresso |
| ❌ Atrasos na entrega final | ✅ Redução drástica de retrabalho |
| ❌ Dificuldades na integração de módulos | ✅ Comunicação alinhada na equipe |

---

# Gestão de Requisitos: Requisito, História e Tarefa

Um projeto Front-End inicia-se com uma ideia que precisa ser lapidada e decomposta até o nível operacional de código:

```text
Ideia Inicial
   ↓
Requisito Geral
   ↓
História de Usuário (User Story)
   ↓
Tarefas Técnicas (Subtarefas)
```

### Decomposição na Prática:

1. **Requisito:** Declaração de alto nível sobre uma funcionalidade ou necessidade do sistema.
   - *Exemplo:* "O sistema deve permitir o gerenciamento de tarefas."
2. **História de Usuário (User Story):** Descrição orientada ao usuário final, focando no valor entregue.
   - *Exemplo:* "Como usuário, quero criar uma tarefa para organizar meu dia a dia."
3. **Tarefas (Subtarefas / Tasks):** Ações técnicas individuais e mensuráveis que os desenvolvedores executam para concluir a história.
   - *Exemplos:*
     - Criar formulário HTML/React;
     - Estilizar o componente de entrada;
     - Validar campos obrigatórios;
     - Integrar a requisição com a API;
     - Escrever testes unitários.

---

# Gestão do Backlog, Prioridade e Estimativa

### 1. Backlog do Produto
O **Backlog** é o repositório dinâmico e centralizado que reúne todas as funcionalidades, melhorias, correções de bugs e tarefas necessárias para desenvolver e evoluir a aplicação.

### 2. Priorização
A priorização determina quais itens do backlog devem ser desenvolvidos primeiro. A equipe alinha os objetivos do produto, o valor para o cliente e as dependências técnicas para focar inicialmente nas funcionalidades mais críticas.

### 3. Estimativa
As estimativas auxiliam a equipe a compreender a complexidade relativa de cada funcionalidade antes de se comprometer com a execução, evitando sobrecargas durante as etapas de desenvolvimento.

---

# Definition of Done (DoD) — Critério de Conclusão

A **Definition of Done (DoD)** estabelece um conjunto claro de critérios de qualidade necessários para declarar que uma tarefa ou funcionalidade está 100% concluída.

Uma funcionalidade no Front-End só é considerada **Done** quando atende a requisitos como:

- [x] Código implementado seguindo os padrões do projeto;
- [x] Testes unitários ou manuais executados com sucesso;
- [x] Revisão de código (*Code Review*) realizada e aprovada;
- [x] Responsividade verificada em diferentes resoluções de tela;
- [x] Integração com a API/Back-end validada sem erros no console.

---

# O Framework Scrum no Front-End

O **Scrum** é um framework ágil amplamente utilizado para o desenvolvimento incremental de produtos complexos, permitindo inspeção e adaptação contínuas.

No contexto Front-End, a adoção do Scrum viabiliza:

- Organização eficiente de requisitos em *User Stories*;
- Divisão do desenvolvimento em ciclos curtos e iterativos chamados **Sprints**;
- Acompanhamento visual das atividades por meio de quadros **Kanban**;
- Distribuição equilibrada de tarefas entre os membros da equipe.

---

# Atividade Prática da Aula

A atividade prática da aula 06 teve como foco a aplicação dos conceitos de gestão agilizada no **Projeto Integrador Interdisciplinar**:

1. **Planejamento de Gestão:** Estruturar a metodologia de gestão de tarefas do projeto do grupo;
2. **Criação do Backlog & Kanban:** Construir o backlog com histórias de usuário, definir prioridades, estimativas de complexidade e organizar o quadro Kanban;
3. **Fluxo de Trabalho & DoD:** Definir o planejamento de Sprints, fluxo de criação de *branches* no Git e os critérios para a *Definition of Done*;
4. **Documentação:** Registrar todo o planejamento de gestão em um arquivo Markdown no repositório e utilizar o board para acompanhar o progresso real do desenvolvimento.

---

# Principais Conceitos Aprendidos

- A gestão de projetos Front-End previne retrabalho, reduz conflitos no versionamento e garante visibilidade do progresso.
- Requisitos devem ser decompostos em Histórias de Usuário e desdobrados em tarefas técnicas operacionais.
- O Backlog organiza e centraliza todas as demandas do sistema para priorização contínua.
- A *Definition of Done* garante rigor de qualidade, assegurando que o código esteja testado, responsivo e integrado antes da publicação.
- O framework Scrum e os quadros Kanban oferecem suporte visual e estruturado para o desenvolvimento em equipe.

---

# Resumo Final

A sexta aula apresentou os fundamentos da gestão de projetos aplicada ao desenvolvimento Front-End. Foi demonstrado como estruturar o ciclo de desenvolvimento desde a concepção de requisitos até o desdobramento em histórias de usuário e tarefas técnicas. Abordou-se a organização do backlog, priorização, estimativas, critérios de qualidade com a *Definition of Done* e a implementação de práticas ágeis com o Scrum e Kanban para orientar o gerenciamento do Projeto Integrador da disciplina.
