
# Aula 05 — Criando APIs para o Front-end

**Disciplina:** Frameworks Front-end
**Professor:** Prof. Me. Deivison S. Takatu

---

# Objetivos da Aula

A quinta aula teve como objetivo apresentar os fundamentos de comunicação entre cliente e servidor, abordando o funcionamento de APIs, protocolo HTTP, formato JSON e a criação prática de um servidor back-end RESTful utilizando Node.js e Express.js integrado ao Front-end, com deploy em nuvem e documentação no Postman.

---

# Contexto da Disciplina

Para que uma aplicação Front-end moderna funcione de forma dinâmica e completa, não basta apenas construir interfaces visuais; é indispensável conectá-las a serviços de back-end capazes de processar regras de negócio e persistir informações.

A aula posiciona o desenvolvimento de APIs como peça-chave na integração de sistemas, permitindo que aplicações clientes (como páginas em React) consumam, enviem, atualizem e excluam dados de forma padronizada via web.

---

# Conteúdos que foram estudados

Durante a aula foram abordados temas essenciais de infraestrutura e desenvolvimento web:

- API (Application Programming Interface)
- Protocolo HTTP e Métodos HTTP
- Endpoints
- Estrutura de dados em JSON
- Servidores Back-end e Web Services
- Framework Express.js (Node.js Puro vs. Express)
- Middlewares (CORS e Body-Parser)
- Implementação de CRUD com persistência em JSON
- Hospedagem e Deploy em Nuvem (Render e Vercel)
- Documentação e Testes de APIs com Postman

---

# Métodos HTTP e Endpoints

A comunicação web apoia-se no protocolo HTTP, estruturado por verbos e rotas de comunicação:

- **Endpoint:** URL específica que atua como ponto de comunicação entre o cliente e o servidor para acessar determinada funcionalidade ou recurso.
- **GET:** Utilizado para recuperar dados do servidor. É um método seguro (não altera dados) e idempotente (múltiplas chamadas geram o mesmo resultado).
- **POST:** Utilizado para criar novos recursos. Não é idempotente (chamadas repetidas duplicam recursos).
- **PUT / PATCH:** Métodos de atualização; o `PUT` substitui o recurso por completo, enquanto o `PATCH` realiza atualizações parciais.
- **DELETE:** Utilizado para remover recursos específicos do servidor (idempotente).

---

# O Formato JSON (JavaScript Object Notation)

O JSON é o padrão universal e leve para troca de informações entre clientes e servidores.

Principais características:

- Fácil leitura e escrita por humanos;
- Rápido e prático para parsear e gerar via código;
- Estruturado em coleções de pares chave/valor (objetos `{}`) e listas ordenadas (arrays `[]`).

---

# Criação de APIs com Express.js

O Express.js é um framework minimalista e popular para Node.js, adotado por abstrair e simplificar o código verboso do módulo HTTP nativo.

Destaques da ferramenta:

- **Roteamento simplificado:** Facilita a declaração de rotas da aplicação (ex.: `/api/notes`);
- **Middlewares essenciais:**
  - `cors`: Mecanismo de segurança configurado para liberar requisições a partir de domínios externos no navegador;
  - `body-parser`: Permite ao servidor ler e decodificar o corpo das requisições enviadas em formato JSON (métodos POST e PUT).

---

# Aplicação Prática: API de Notas (CRUD)

Para fixação prática, foi desenvolvido um projeto completo de gerenciamento de notas utilizando o módulo de arquivos do Node (`fs`) para armazenar dados em um arquivo `data.json`:

| Operação               | Método HTTP | Endpoint           | Descrição da Ação                                                               |
| :----------------------- | :----------- | :----------------- | :---------------------------------------------------------------------------------- |
| **Listar Notas**   | `GET`      | `/api/notes`     | Lê o arquivo e retorna todas as notas cadastradas.                                 |
| **Obter por ID**   | `GET`      | `/api/notes/:id` | Retorna os detalhes de uma única nota filtrada por ID.                             |
| **Criar Nota**     | `POST`     | `/api/notes`     | Recebe`titulo` e `texto`, cria ID único via `Date.now().toString()` e salva. |
| **Atualizar Nota** | `PUT`      | `/api/notes/:id` | Atualiza o conteúdo da nota existente ou retorna status 404 caso não encontrada.  |
| **Excluir Nota**   | `DELETE`   | `/api/notes/:id` | Remove o registro selecionado e persiste as mudanças.                              |

---

# Deploy e Hospedagem em Nuvem

Para simular o ambiente de produção e publicação profissional, utilizou-se:

- **Render:** Plataforma de nuvem para hospedar o back-end em Node.js com deploy contínuo direto do GitHub. O comando de start é configurado via terminal web (`node server.js` ou `node api.js`).
- **Vercel:** Plataforma utilizada para hospedar a interface gráfica em React, conectando-a à URL pública gerada no Render.

---

# Documentando e Testando com Postman

Uma boa API deve possuir documentação clara detalhando métodos, endpoints, parâmetros e formatos de retorno.

- **Postman:** Ferramenta interativa que substitui chamadas manuais via terminal por uma interface amigável para envio de requisições HTTP.
- Permite criar **Collections** estruturadas, definir variáveis de ambiente, simular respostas (Mock Servers) e automatizar testes de integração.

---

# Questões para Refletir

A aula propôs pontos de análise crítica sobre o código desenvolvido:

1. **Segurança:** Riscos de usar liberação aberta de CORS (`*`) e ausência de sanitização/validação dos dados no corpo das requisições.
2. **Persistência em JSON (`fs`):** Uso simples para fins didáticos, porém inviável em produção por não gerenciar concorrência de escritas e bloquear o processamento.
3. **Escalabilidade:** Limitações severas de performance e memória caso o arquivo atinja 10.000 registros ou mais.
4. **Organização da Arquitetura:** Problemas de manter toda a lógica e rotas centralizadas apenas no `server.js`, em vez de modularizar em controllers, rotas e serviços.

---

# Atividades da Aula

### Atividade 01

1. Atualizar o repositório da disciplina com os arquivos iniciais do Express;
2. Enviar o link do repositório atualizado por meio do formulário indicado.

### Atividade 02

1. Criar o back-end completo com Express e persistência em arquivo JSON;
2. Realizar o deploy do back-end na plataforma Render;
3. Desenvolver o Front-end em React consumindo todas as operações do CRUD da API e publicá-lo na Vercel;
4. Criar uma **Collection no Postman** documentando as quatro operações CRUD com suas respectivas descrições e códigos de resposta;
5. Consolidar prints do código, da aplicação rodando e links do projeto para entrega na plataforma acadêmica.

---

# Principais Conceitos Aprendidos

- APIs REST organizam a comunicação entre front-end e back-end por meio de padrões universais do protocolo HTTP.
- Métodos como GET, POST, PUT e DELETE possuem regras claras de finalidade e idempotência.
- O Express.js torna a criação de servidores em Node.js ágil através de rotas declarativas e middlewares.
- Publicação contínua (Deploy) em serviços como Render e Vercel aproxima o fluxo de desenvolvimento das práticas de mercado.
- A documentação e os testes estruturados no Postman garantem a confiabilidade e facilidade de integração das APIs por outras equipes.

---

# Resumo Final

A quinta aula aprofundou a conexão entre o front-end e a camada de serviços web por meio da construção prática de uma API REST com Express.js e Node.js. Foi desenvolvido um CRUD funcional completo de notas persistido em JSON, acompanhado pelo deploy simultâneo das pontas do sistema (Back-end no Render e Front-end na Vercel), além da homologação, testes e documentação dos endpoints por meio do Postman, integrando infraestrutura, boas práticas e desenvolvimento full-stack.
