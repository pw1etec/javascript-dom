# 🌐 Manipulando a DOM (Document Object Model)

> Um guia super completo, visual e cheio de curiosidades ⭐

---

## 🤔 O que é a DOM?

A **DOM** é a sigla para **Document Object Model**. Ela representa toda a estrutura de uma página web como uma **árvore de objetos em memória**, que o JavaScript pode acessar e manipular. É como se o navegador pegasse o HTML e transformasse numa árvore de nós que você pode ler, alterar, adicionar ou remover.

> Imagine a página como uma **árvore genealógica digital** onde cada elemento HTML é um "membro" da família DOM. 🌳

---

## 🌳 Representação Visual da Árvore DOM

![Árvore DOM - Exemplo visual](./assets/images/dom-tree-example_hu17403287862339183890.jpg)

🔗 Fonte: [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

### Exemplo de HTML:

```html
<html>
  <head>
    <title>Minha Página</title>
  </head>
  <body>
    <h1>Título</h1>
    <p>Texto</p>
  </body>
</html>
```

### Visual em árvore:

```
Document
└── html
    ├── head
    │   └── title
    │       └── Texto: "Minha Página"
    └── body
        ├── h1
        │   └── Texto: "Título"
        └── p
            └── Texto: "Texto"
```

---

## 🧩 Tipos de Nós (Nodes) da DOM

| Tipo de nó      | Código | Descrição                  |
| --------------- | ------ | -------------------------- |
| `ELEMENT_NODE`  | 1      | Qualquer elemento HTML     |
| `TEXT_NODE`     | 3      | Texto dentro de elementos  |
| `COMMENT_NODE`  | 8      | Comentários `<!-- ... -->` |
| `DOCUMENT_NODE` | 9      | O próprio `document`       |

### Curiosidade:

```js
const titulo = document.querySelector("h1");
console.log(titulo.nodeType); // 1 (ELEMENT_NODE)
```

---

## 🌍 `window`: O Universo do Navegador

O `window` é o **objeto global** em qualquer página. Ele representa a janela do navegador e tudo que está dentro dela, incluindo `document`, `alert`, `setTimeout`, e muito mais.

### Curiosidades legais:

```js
window.alert("Olá do universo!");
console.log(window.innerWidth); // largura da janela
console.log(window.location.href); // URL atual
```

✅ Tudo que é global no navegador está dentro de `window`. Por exemplo:

```js
alert === window.alert // true
```

🔗 [MDN: window](https://developer.mozilla.org/pt-BR/docs/Web/API/Window)

---

## 📄 `document`: A Porta de Entrada para a DOM

O `document` representa o HTML carregado e é nosso ponto de entrada para acessar e manipular os elementos da página.

### Teste agora no DevTools:

```js
document.title = "Título alterado via JS";
document.body.style.background = "linear-gradient(#000, #444)";
document.querySelector("h1").textContent = "Você DOMina!";
document.images; // lista de imagens na página
document.links;  // todos os <a>
```

🔗 [MDN: document](https://developer.mozilla.org/pt-BR/docs/Web/API/Document)

---

## 🕹️ Ferramentas Escondidas no DevTools

### Atalhos de Console:

| Comando     | O que faz                                             |
| ----------- | ----------------------------------------------------- |
| `$0`        | Último elemento inspecionado                          |
| `$$('tag')` | Seleciona múltiplos elementos como `querySelectorAll` |
| `dir(obj)`  | Exibe propriedades interativas de objetos             |

```js
$0.style.border = "2px dashed red";
console.dir(document.body);
```

---

## 🛠️ Selecionando e Manipulando Elementos

### 🔎 Seletores:

```js
document.getElementById("meu-id")
document.getElementsByClassName("minha-classe")
document.querySelector("#meu-id")
document.querySelectorAll(".minha-classe")
```

### 🖊️ Modificando conteúdo:

```js
el.textContent = "Novo texto";
el.innerHTML = "<strong>HTML aqui</strong>";
```

### 🎨 Estilizando:

```js
el.style.backgroundColor = "pink";
el.style.transform = "rotate(5deg)";
```

### 🎯 Atributos:

```js
el.setAttribute("title", "Dica de toolip");
el.removeAttribute("disabled");
```

---

## 🧪 Criando e Inserindo Elementos Complexos

### Criando uma estrutura DOM completa via JS:

```js
const card = document.createElement("div");
card.className = "card";

const titulo = document.createElement("h2");
titulo.textContent = "Título do Card";

const descricao = document.createElement("p");
descricao.textContent = "Descrição gerada com JavaScript!";

card.appendChild(titulo);
card.appendChild(descricao);
document.body.appendChild(card);
```

### Resultado: Um novo "card" aparece na página!

> 🌟 Você pode criar menus, seções inteiras, carrosséis e até mini aplicativos usando esse princípio.

---

## 🔁 Clonando, Movendo e Removendo

```js
const clone = card.cloneNode(true);
document.body.appendChild(clone);

card.remove(); // remove o original
```

### Outras formas de inserção:

```js
el.before(outroElemento);
el.after(outroElemento);
el.prepend(filho);
el.append(filho);
```

---

## 🎯 Eventos: Interatividade na Veia

```js
const btn = document.querySelector("button");
btn.addEventListener("click", () => {
  alert("Você clicou!");
});
```

### Eventos comuns:

* `click`
* `dblclick`
* `mouseover`
* `keydown`
* `submit`

🔗 [MDN: Eventos](https://developer.mozilla.org/pt-BR/docs/Web/Events)

---

## 🧙‍♂️ Exemplo Interativo Completo

```html
<h1 id="titulo">Bem-vindo</h1>
<button onclick="criarCard()">Gerar Card</button>

<script>
function criarCard() {
  const card = document.createElement("div");
  card.className = "card";
  card.style.padding = "10px";
  card.style.border = "1px solid #aaa";
  card.style.margin = "10px 0";

  const titulo = document.createElement("h3");
  titulo.textContent = "Novo Elemento";

  const agora = document.createElement("p");
  agora.textContent = `Criado em: ${new Date().toLocaleTimeString()}`;

  card.appendChild(titulo);
  card.appendChild(agora);
  document.body.appendChild(card);
}
</script>
```

---

## 📚 Documentações Oficiais

* [📘 DOM - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model)
* [📗 document - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Document)
* [📙 window - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Window)
* [📕 Node - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Node)
* [📒 Element - MDN](https://developer.mozilla.org/pt-BR/docs/Web/API/Element)
* [🧾 Eventos - MDN](https://developer.mozilla.org/pt-BR/docs/Web/Events)

---

## 🚀 Curiosidades e Desafios para Alunos

* Sabia que você pode **criar seu próprio console.log visual** na tela com `document.createElement("pre")`?
* Que tal tentar fazer um **to-do list** 100% dinâmica usando a DOM?
* Experimente explorar o `document.body.childNodes` e iterar pelos nós!

> Curiosidade: `document.all` é uma relíquia da web antiga. Funciona... mas é obsoleto! ❌

---

## ✅ Conclusão

A DOM é a ponte entre o HTML e o JavaScript. Ao entender sua estrutura e como manipulá-la, você desbloqueia o verdadeiro poder do Front-End!

> DOM não é só código — é magia interativa 🪄

👨‍🏫 Criado para os alunos da **ETEC**  por **[Prof. Alessandro](https://github.com/alevitorio)**
