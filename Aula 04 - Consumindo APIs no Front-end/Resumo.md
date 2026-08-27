
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
- Utilização de mensagens para troca de informações.

### Métodos HTTP

| Método    | Finalidade                          |
| ---------- | ----------------------------------- |
| `GET`    | Recuperar informações             |
| `POST`   | Criar novos recursos                |
| `PUT`    | Substituir completamente um recurso |
| `PATCH`  | Atualizar parcialmente um recurso   |
| `DELETE` | Remover um recurso                  |

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
