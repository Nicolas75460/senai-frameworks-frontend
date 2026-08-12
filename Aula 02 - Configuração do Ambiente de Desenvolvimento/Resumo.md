# Aula 02 — Configuração do Ambiente de Desenvolvimento

> **Disciplina:** Frameworks Front-end
> **Professor:** Prof. Me. Deivison S. Takatu

## 1. Versionamento

**Versionamento** é o processo de identificar e registrar diferentes versões de um software, permitindo acompanhar **o que foi alterado, por quem e quando**. Diferentemente de um backup, ele mantém um histórico detalhado das alterações e permite colaboração entre desenvolvedores e reversão granular de mudanças. 

### Benefícios

* Histórico completo das alterações;
* Rastreabilidade e auditoria;
* Trabalho simultâneo entre desenvolvedores;
* Recuperação de versões anteriores;
* Redução de retrabalho;
* Maior segurança durante o desenvolvimento. 

---

## 2. Versionamento Semântico (SemVer)

O **Semantic Versioning (SemVer)** utiliza o padrão:

```text
MAJOR.MINOR.PATCH
```

| Componente | Significado                    | Exemplo |
| ---------- | ------------------------------ | ------- |
| **MAJOR**  | Mudanças incompatíveis         | `2.0.0` |
| **MINOR**  | Nova funcionalidade compatível | `1.1.0` |
| **PATCH**  | Correção de bugs               | `1.0.1` |

Por exemplo:

```text
1.0.0 → Primeira versão estável
1.1.0 → Nova funcionalidade
1.1.1 → Correção de bug
2.0.0 → Mudança incompatível
```

O SemVer facilita a gestão de dependências, melhora a compreensão das mudanças e torna a evolução do software mais previsível.  

---

## 3. Git e Controle de Versão

**Git** é um sistema de controle de versão utilizado para registrar alterações nos arquivos de um projeto.

Com ele é possível:

* Criar histórico de versões;
* Acompanhar alterações;
* Restaurar versões anteriores;
* Sincronizar projetos com repositórios online;
* Trabalhar em equipe. 

Configuração inicial:

```bash
git config --global user.name "<Nome>"
git config --global user.email "<Email>"
```

Para verificar a instalação:

```bash
git --version
```

---

## 4. Tags e Branches

### Tags

As **tags** identificam pontos importantes do histórico, normalmente utilizados para marcar versões ou releases.

Exemplo:

```bash
git tag 1.0.0
git push origin 1.0.0
```

Existem tags **leves (lightweight)** e **anotadas (annotated)**. 

### Branches

Branches permitem desenvolver funcionalidades ou correções isoladamente sem modificar diretamente a versão principal do projeto.

Uma boa prática é manter a branch principal estável e utilizar branches separadas para novas funcionalidades e correções. 

---

## 5. Boas Práticas com Git

Algumas práticas importantes:

* Fazer commits pequenos e frequentes;
* Utilizar mensagens de commit claras;
* Utilizar branches para novas funcionalidades;
* Manter a branch principal estável;
* Executar testes antes de realizar merges. 

Exemplos de tipos de alterações:

* `Bug Fix`
* `New Feature`
* `Feature Enhancement`
* `Refactoring`
* `Performance`
* `Security Patch`
* `Dependency Update`
* `Adding Tests` 

---

## 6. IDE e Visual Studio Code

Uma **IDE (Integrated Development Environment)** reúne ferramentas para desenvolver, executar, testar e depurar software.

O **Visual Studio Code (VS Code)** é um editor de código que, através de extensões e ferramentas integradas, oferece diversos recursos normalmente encontrados em IDEs. 

---

## 7. Node.js

O **Node.js** é um ambiente de execução JavaScript que permite executar código no servidor.

Uma de suas principais vantagens é possibilitar o uso de **JavaScript tanto no navegador quanto no servidor**, facilitando a integração entre Front-end e Back-end. 

Para verificar a instalação:

```bash
node --version
```

---

## 8. NPM

O **NPM (Node Package Manager)** é o gerenciador de pacotes do Node.js.

Ele permite:

* Instalar bibliotecas;
* Atualizar dependências;
* Remover pacotes;
* Gerenciar frameworks;
* Compartilhar módulos;
* Automatizar a configuração das dependências.

O arquivo `package.json` registra as dependências e configurações do projeto. Assim, outro desenvolvedor pode executar:

```bash
npm install
```

para instalar automaticamente os pacotes necessários. 

---

## 9. Criação de um Projeto React

A aula apresenta a criação de um projeto React utilizando `create-react-app`.

### Criar o projeto

```bash
npx create-react-app meu-projeto-react
```

### Entrar na pasta

```bash
cd meu-projeto-react
```

### Abrir no VS Code

```bash
code .
```

### Executar o projeto

```bash
npm start
```

O `npx` executa pacotes do NPM, enquanto o `create-react-app` gera a estrutura inicial da aplicação. 

### Estrutura básica

```text
meu-projeto-react/
├── node_modules/
├── public/
├── src/
├── .gitignore
├── package.json
└── package-lock.json
```

O `src` contém os arquivos da aplicação React, enquanto `node_modules` contém as dependências instaladas. O `package.json` e o `package-lock.json` armazenam informações relacionadas aos pacotes e configurações do projeto. 

---

## 10. Deploy

**Deploy** é o processo de colocar uma aplicação em produção, tornando-a acessível aos usuários.

Etapas comuns:

1. Compilação;
2. Configuração do ambiente;
3. Testes finais;
4. Publicação. 

### Vercel

A **Vercel** é uma plataforma utilizada para hospedagem e deploy de aplicações web modernas.

Principais características apresentadas:

* Integração com GitHub, GitLab e Bitbucket;
* Deploy automático após `push`;
* Suporte a frameworks modernos;
* Rollback;
* Serverless Functions;
* CDN global;
* Escalabilidade automática. 

---

## 11. Fluxo Prático da Aula

A atividade proposta consiste em desenvolver uma aplicação React seguindo o fluxo:

```text
React
  ↓
VS Code
  ↓
Git
  ↓
GitHub
  ↓
Vercel
  ↓
Aplicação Online
```

O projeto deve ser desenvolvido no VS Code, versionado utilizando Git, enviado para um repositório no GitHub e posteriormente conectado à Vercel para realizar o deploy automático. 

---

## 12. Conclusão

A aula apresentou as principais ferramentas necessárias para iniciar o desenvolvimento de aplicações Front-end modernas:

* **Git** → controle de versões;
* **GitHub** → hospedagem e colaboração com repositórios;
* **VS Code** → ambiente de desenvolvimento;
* **Node.js** → execução do JavaScript;
* **NPM** → gerenciamento de dependências;
* **React** → desenvolvimento de interfaces;
* **Vercel** → deploy e hospedagem.

O principal fluxo aprendido foi **desenvolver → versionar → publicar no GitHub → realizar deploy na Vercel**, estabelecendo uma base para o desenvolvimento profissional de aplicações Front-end.
