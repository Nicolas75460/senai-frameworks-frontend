# Aula 07 — Frameworks CSS

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu  

---

# Objetivos da Aula

A sétima aula abordou a evolução da estilização no desenvolvimento Web, consolidando os fundamentos do CSS (*Cascading Style Sheets*), formas de aplicação, propriedades essenciais, a estrutura do *Box Model*, layouts responsivos com *Flexbox* e introduzindo o uso de Frameworks CSS com ênfase no paradigma *Utility-First* do **Tailwind CSS**.

---

# Contexto da Disciplina

Estilizar aplicações web modernas exige conciliar estética visual, organização de código e responsividade em múltiplos dispositivos. 

Embora o CSS puro ofereça controle total sobre a interface, a estilização manual de projetos grandes pode se tornar repetitiva e difícil de manter. A introdução de Frameworks CSS como o Tailwind permite acelerar a construção de componentes visuais mantendo um padrão de design consistente e escalável.

---

# Fundamentos do CSS (Cascading Style Sheets)

O CSS é a linguagem responsável por definir a apresentação visual das páginas HTML. Além de cores e fontes, ele gerencia margens, alinhamentos, larguras, alturas e o comportamento de elementos na tela.

### Sintaxe Básica
O CSS é composto por regras declarativas na estrutura:

```css
seletor {
  propriedade: valor;
}
```

- **Seletor:** Indica qual elemento HTML receberá o estilo (ex.: `body`, `p`, `.card`, `#header`);
- **Propriedade:** Atributo que será modificado (ex.: `background-color`, `font-size`);
- **Valor:** Configuração atribuída à propriedade (ex.: `#FF0000`, `16px`).

---

# Formas de Aplicação do CSS

| Modalidade | Sintaxe / Local | Uso Recomendado |
| :--- | :--- | :--- |
| **In-Line** | Atributo `style="..."` na própria tag HTML | Testes rápidos ou ajustes pontuais de urgência. |
| **Interno** | Tag `<style>` dentro do `<head>` do arquivo HTML | Páginas únicas ou protótipos de página única. |
| **Externo** | Arquivo `.css` separado e vinculado via `<link rel="stylesheet">` | **Boa prática padrão:** centraliza estilos e permite reuso. |

---

# Propriedades Essenciais, Classes e IDs

### Propriedades Frequentes:
- `color` & `background-color`: Definição de cores de texto e fundo;
- `font-family` & `font-size`: Tipografia e dimensionamento de texto;
- `margin` & `padding`: Espaçamentos externo e interno;
- `border`: Espessura, estilo e cor das bordas;
- `width` & `height`: Dimensões dos elementos;
- `display`: Forma de renderização (`block`, `inline`, `flex`, `grid`, `none`);
- `position`: Método de posicionamento (`static`, `relative`, `absolute`, `fixed`);
- `text-align`: Alinhamento horizontal de texto.

### Diferenças entre Classes e IDs:
- **Classes (`.nome-classe`):** Utilizadas para aplicar o mesmo conjunto de estilos a múltiplos elementos na página, garantindo padronização e reuso.
- **IDs (`#nome-id`):** Identificadores únicos aplicados a um único elemento, úteis para seções específicas, ancoragem de navegação ou manipulação via JavaScript.

---

# O Modelo de Caixas (Box Model)

O **Box Model** é o conceito fundamental do CSS que descreve como cada elemento HTML é representado como uma caixa retangular composta por 4 camadas:

```text
+-----------------------------------+
|               MARGIN              |
|  +-----------------------------+  |
|  |           BORDER            |  |
|  |  +-----------------------+  |  |
|  |  |        PADDING        |  |  |
|  |  |  +-----------------+  |  |  |
|  |  |  |     CONTENT     |  |  |  |
|  |  |  +-----------------+  |  |  |
|  |  +-----------------------+  |  |
|  +-----------------------------+  |
+-----------------------------------+
```

1. **Content:** Área onde o texto, imagens ou elementos filhos são exibidos;
2. **Padding:** Espaço interno entre o conteúdo e a borda;
3. **Border:** Linha delimitadora que envolve o padding e o conteúdo;
4. **Margin:** Espaço externo fora da borda, criando distância em relação a outros elementos.

---

# Flexbox e Layouts Responsivos

O **Flexbox (Flexible Box Layout)** é um módulo de layout unidimensional projetado para alinhar e distribuir espaços entre elementos em linhas ou colunas de forma dinâmica.

### Principais Propriedades do Flexbox:
- `display: flex;` — Habilita o contexto flexível no elemento pai;
- `flex-direction: row | column;` — Define o eixo principal de alinhamento;
- `justify-content: flex-start | center | space-between | space-around;` — Alinhamento no eixo principal;
- `align-items: flex-start | center | flex-end;` — Alinhamento no eixo transversal;
- `flex-wrap: wrap;` — Permite a quebra automáticas de linha;
- `gap: 16px;` — Define o espaçamento entre itens flexíveis.

---

# O que é um Framework CSS?

Um **Framework CSS** é um conjunto pré-estruturado de arquivos, regras de estilo, grids e componentes visuais (como botões, cards, menus e formulários) que visa agilizar o processo de desenvolvimento e garantir consistência gráfica.

### O Problema do CSS Manual:
No CSS tradicional, cada botão, formulário ou regra de responsividade precisa ser escrito do zero. Isso gera arquivos extensos, repetição de código e dificulta a manutenção em projetos de grande porte.

---

# Tailwind CSS e a Abordagem Utility-First

O **Tailwind CSS** é um framework moderno baseado no conceito **Utility-First**. Em vez de entregar componentes prontos rígidos, ele disponibiliza classes utilitárias de baixa abstração e responsabilidade única.

```html
<!-- Exemplo de botão criado com Tailwind CSS -->
<button class="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition">
  Enviar
</button>
```

### Vantagens da Abordagem Utility-First:
- **Agilidade:** Estilização rápida diretamente no arquivo HTML/JSX;
- **Flexibilidade:** Permite criar layouts exclusivos sem depender de componentes pré-formatados;
- **Customização:** Fácil ajuste de tokens de design (cores, espaçamentos, tipografia);
- **Mobile-First Nativo:** Suporte simples para telas responsivas usando prefixos como `sm:`, `md:`, `lg:`.

---

# Formas de Integração do Tailwind CSS

1. **Play CDN (Ideal para testes rápidos):**
   ```html
   <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
   ```
2. **Tailwind CLI / PostCSS (Ideal para produção):**
   - Instalação via npm: `npm install tailwindcss @tailwindcss/cli`
   - Inclusão no arquivo CSS principal: `@import "tailwindcss";`
   - Integração com frameworks como React, Vite, Next.js, Angular, etc.
3. **Tailwind IntelliSense:**
   - Extensão do VS Code que fornece autocompletar de classes utilitárias e prévia dos estilos CSS correspondentes.

---

# Atividades Práticas da Aula

### Atividade 01: Fixação com CSS Puro e Flexbox
1. Criar projeto HTML com CSS Externo (`<link>`);
2. Inserir 20 elementos e configurar propriedades de Content, Padding, Border e Margin;
3. Aplicar 20 propriedades de Flexbox para organizar os elementos de forma responsiva.

### Atividade 02: Projeto com Tailwind CSS
1. Desenvolver uma interface utilizando no mínimo **30 classes diferentes do Tailwind CSS** (abrangendo cores, tipografia, espaçamento, dimensões, bordas, flexbox/grid e responsividade);
2. Publicar no GitHub e documentar com um arquivo Markdown (`README.md`) contendo prints do código, da aplicação rodando, listagem explicativa das 30 classes e o link do repositório.

---

# Principais Conceitos Aprendidos

- O CSS organiza a camada visual da Web através de seletores, propriedades e valores.
- O *Box Model* (Content, Padding, Border, Margin) é essencial para controle de dimensões e espaçamento.
- O *Flexbox* facilita o alinhamento e a distribuição responsiva de elementos na tela.
- Frameworks CSS reduzem a repetição e aceleram a construção de interfaces.
- O Tailwind CSS utiliza a abordagem *Utility-First*, combinando pequenas classes de responsabilidade única para construir componentes dinâmicos e altamente customizáveis.

---

# Resumo Final

A sétima aula apresentou a transição do CSS tradicional para o uso moderno de Frameworks CSS. Foram revisados os conceitos fundamentais de estilização, aplicação externa, seletores, modelo de caixas (Box Model) e layouts flexíveis com Flexbox. Em seguida, foi introduzido o Tailwind CSS e a abordagem *Utility-First*, demonstrando como utilizar classes utilitárias diretamente no código para construir interfaces responsivas, consistentes e escaláveis de maneira ágil.
