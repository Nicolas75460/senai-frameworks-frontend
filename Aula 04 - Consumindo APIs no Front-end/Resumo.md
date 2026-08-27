# Aula 04 — Consumindo APIs no Front-end

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu  

---

## 1. API — Application Programming Interface

Uma **API** é um conjunto de protocolos, rotinas e ferramentas que define como diferentes componentes de software devem se comunicar.

No desenvolvimento Web, as APIs permitem que o **Front-end** se comunique com servidores, bancos de dados e outros serviços.

---

## 2. REST

**REST (Representational State Transfer)** é um estilo arquitetural utilizado principalmente no desenvolvimento de sistemas distribuídos na Web.

### Principais princípios
- Comunicação cliente-servidor **stateless**;
- Utilização dos métodos HTTP;
- Recursos identificados por **URIs**;
- Representação dos dados, como **JSON**.

---

## 3. Protocolo HTTP

O **HTTP (Hypertext Transfer Protocol)** é o protocolo responsável pela comunicação entre clientes e servidores na Web.

### Principais características
- **Cliente-servidor:** o navegador realiza requisições ao servidor;
- **Stateless:** cada requisição é independente;
- Comunicação baseada em mensagens.

### Métodos HTTP

| Método | Finalidade |
| :--- | :--- |
| `GET` | Recuperar informações |
| `POST` | Criar novos recursos |
| `PUT` | Substituir completamente um recurso |
| `PATCH` | Atualizar parcialmente um recurso |
| `DELETE` | Remover um recurso |

---

## 4. Funcionamento de uma Requisição

O fluxo básico entre Front-end e Backend ocorre da seguinte maneira:

```text
Usuário
   ↓
Front-end / Navegador
   ↓
Requisição HTTP
   ↓
Servidor / API
   ↓
Banco de Dados ou Serviço Externo
   ↓
Resposta JSON
   ↓
Front-end
   ↓
Atualização da Interface
```

O servidor recebe a requisição, identifica a rota, executa a lógica necessária e retorna uma resposta para o Front-end.

---

## 5. Endpoint

Um **endpoint** é uma URL específica utilizada para acessar determinado recurso ou funcionalidade de uma API.

Ele representa o ponto de comunicação entre o cliente e o servidor.

### Exemplos
- `GET /users`
- `POST /users`
- `PUT /users/1`
- `DELETE /users/1`

Cada endpoint pode representar uma operação diferente sobre os recursos da aplicação.

---

## 6. APIs Públicas

APIs públicas podem ser utilizadas para estudar integração entre aplicações e desenvolver projetos reais.

Existem catálogos que reúnem APIs disponibilizadas por diferentes projetos e serviços, facilitando a busca por fontes de dados para aplicações.

---

## 7. JSON

**JSON (JavaScript Object Notation)** é um formato leve utilizado para troca de dados entre sistemas.

### Características
- Fácil leitura por humanos;
- Fácil processamento por máquinas;
- Utiliza objetos;
- Utiliza arrays.

### Exemplo
```json
{
  "nome": "Nícolas",
  "idade": 18,
  "curso": "Programação"
}
```

---

## 8. Servidor Backend

O servidor Backend é responsável por processar requisições, gerenciar dados e fornecer respostas para clientes como navegadores e aplicações.

### Principais funções
- Armazenar e recuperar dados;
- Executar regras de negócio;
- Fornecer APIs;
- Processar requisições;
- Retornar respostas ao cliente.

---

## 9. Web Service

Um **Web Service** é um serviço acessível pela Web que permite a comunicação entre diferentes sistemas utilizando protocolos como HTTP/HTTPS.

Ele permite que sistemas desenvolvidos com diferentes linguagens, plataformas e tecnologias se comuniquem de forma padronizada.

---

## 10. Express.js

O **Express.js** é um framework para Node.js utilizado para facilitar a criação de servidores Web e APIs.

### Características
- Minimalista;
- Flexível;
- Leve;
- Popular no ecossistema JavaScript.

### Principais recursos
- Criação de rotas;
- Middlewares;
- Integração com bancos de dados;
- Criação de APIs REST;
- Tratamento de requisições e respostas.

---

## 11. CORS

**CORS (Cross-Origin Resource Sharing)** é um mecanismo de segurança utilizado pelos navegadores para controlar o acesso entre diferentes origens.

Quando o Front-end e o Backend estão hospedados em origens diferentes, o CORS precisa ser configurado corretamente para permitir a comunicação.

---

## 12. Criando uma API REST com Express

O processo apresentado na aula utiliza Node.js + Express.js.

### Instalar o Express
```bash
npm install express
```

### Instalar o CORS
```bash
npm install cors express
```

### Executar a API
```bash
node api.js
```

O arquivo `api.js` contém a configuração do servidor e suas respectivas rotas.

---

## 13. Quando utilizar Express.js?

O Express.js pode ser utilizado para:
- APIs REST;
- Backends para aplicações Web;
- Backends para aplicações Mobile;
- Integração com bancos de dados;
- Aplicações escaláveis;
- Prototipagem rápida;
- Autenticação;
- Logs;
- Tratamento de erros.

> **Nota:** Para aplicações em tempo real ou processamento pesado, podem ser necessárias tecnologias mais específicas, como WebSockets e Workers.

---

## 14. Deploy com Render

O **Render** é uma plataforma de hospedagem em nuvem que permite publicar aplicações e Web Services.

### Recursos apresentados
- Integração com Git;
- Deploy automático;
- Suporte a Node.js e Python;
- Escalabilidade;
- SSL gratuito;
- Monitoramento;
- Hospedagem de APIs e microsserviços.

### Fluxo de Deploy
```text
GitHub
   ↓
Render
   ↓
Web Service
   ↓
API Online
```

### Etapas
1. Fazer commit do projeto no GitHub;
2. Criar uma conta no Render;
3. Criar um Web Service;
4. Conectar o repositório do GitHub;
5. Configurar os comandos de execução;
6. Realizar o deploy.

---

## 15. Atividade Prática

A atividade consiste em criar uma API REST utilizando Express.js que disponibilize uma rota para consulta de data e hora.

### Requisitos
- Criar uma API utilizando Express;
- Criar uma rota de data e hora;
- Fazer o deploy da API no Render;
- Desenvolver um Front-end separado;
- Consumir a API pelo Front-end;
- Exibir a data e hora na interface.

Além disso, a API e o Front-end deverão estar organizados em repositórios separados.

### A documentação deverá conter:
- Prints do código;
- Prints da aplicação funcionando;
- Prints dos painéis do Render e Vercel;
- Links dos repositórios no GitHub.

---

## 16. Fluxo Geral da Aula

```text
                 ┌──────────────┐
                 │   Usuário    │
                 └──────┬───────┘
                        ↓
                 ┌──────────────┐
                 │  Front-end   │
                 └──────┬───────┘
                        ↓
                  HTTP Request
                        ↓
                 ┌──────────────┐
                 │   Endpoint   │
                 └──────┬───────┘
                        ↓
                 ┌──────────────┐
                 │ Express.js   │
                 │   Backend    │
                 └──────┬───────┘
                        ↓
                 ┌──────────────┐
                 │ Processamento│
                 └──────┬───────┘
                        ↓
                  JSON Response
                        ↓
                 ┌──────────────┐
                 │  Front-end   │
                 └──────┬───────┘
                        ↓
                 Interface atualizada
```

---

## 17. Conclusão

A aula apresentou o processo de comunicação entre Front-end e Backend através de APIs.

### Principais conceitos
- **API** → interface de comunicação entre sistemas;
- **REST** → estilo arquitetural para APIs Web;
- **HTTP** → protocolo de comunicação;
- **Endpoint** → ponto de acesso a um recurso;
- **JSON** → formato de troca de dados;
- **Express.js** → framework para criação de APIs com Node.js;
- **CORS** → mecanismo de controle de acesso entre diferentes origens;
- **Render** → plataforma utilizada para hospedagem e deploy.

### O principal fluxo aprendido foi:

```text
Front-end
    ↓
HTTP Request
    ↓
Endpoint
    ↓
Express.js / Backend
    ↓
Processamento
    ↓
JSON Response
    ↓
Front-end
    ↓
Interface atualizada
```

Esse fluxo permite separar a interface do usuário da lógica e dos dados do sistema, sendo uma estrutura fundamental para aplicações Web modernas.
