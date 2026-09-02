# EcoTrend 🌱
 
E-commerce fictício de produtos sustentáveis, construído em React + Vite como projeto de checkpoint. Simula um fluxo completo de loja: listagem de produtos com filtro por categoria, carrinho lateral persistente e finalização de compra.
 
## Funcionalidades
 
- **Catálogo de produtos** carregado via fetch de um `produtos.json` local, simulando uma API.
- **Filtro por categoria** (Todas / Objetos / Roupas), aplicado dinamicamente sobre a lista renderizada.
- **Carrinho lateral (sidebar)**, com contador de itens no header e persistência em `localStorage` — o carrinho sobrevive a um refresh da página.
- **Checkout simulado**, com estado de carregamento (spinner) e mensagens de sucesso/erro, incluindo geração de número de pedido e cálculo de total.
- **Layout responsivo** com header, footer e seção de produtos organizados em componentes isolados.
## Stack
 
- [React 19](https://react.dev/)
- [Vite](https://vitejs.dev/) como bundler e dev server
- ESLint configurado com regras de React Hooks e React Refresh
- Sem backend real — dados de produtos vêm de um JSON estático e o checkout é uma Promise simulada com `setTimeout`
## Estrutura do projeto
 
```
src/
├── components/
│   ├── Header.jsx      # marca, navegação e ícone do carrinho
│   ├── Produtos.jsx     # listagem e filtro de produtos
│   ├── Carrinho.jsx     # sidebar do carrinho e checkout
│   └── Footer.jsx       # rodapé
├── services/
│   ├── produtosApi.js   # busca dos produtos (fetch simulando API)
│   ├── carrinho.js      # manipulação direta do DOM para cards do carrinho e filtro
│   └── checkout.js      # simulação assíncrona de finalização de compra
├── App.jsx               # composição dos componentes e estado global do carrinho
└── main.jsx
produtos.json              # dados mockados do catálogo
```
 
## Detalhe técnico: DOM manipulado + estado do React
 
Este projeto mistura intencionalmente duas abordagens no carrinho e no filtro de produtos:
 
- O **estado React** (`useState` + `localStorage`) controla dados que precisam sobreviver a re-renders e re-carregamentos: contador de itens, conteúdo persistido do carrinho.
- Funções em `services/carrinho.js` manipulam o **DOM diretamente** (via `useRef`) para inserir os cards visuais no carrinho e aplicar o filtro de categoria, sem passar pelo ciclo de render do React.

## Como rodar localmente
 
```bash
# instalar dependências
npm install
 
# rodar em modo desenvolvimento
npm run dev
 
# gerar build de produção
npm run build
 
# rodar lint
npm run lint
```
 
O projeto sobe por padrão em `http://localhost:5173`.
---
## Integrantes
- Nome: Allan Ragazzo Freire / Rm: 569534
- Nome: Danillo Roque Souza Machado / Rm: 573831
- Nome: Leonardo Scalisse Silva / Rm: 569114
- Nome: Pietro Schimidt Ruotolo / Rm: 570632
- Nome: Valdemar da Rocha Formiga neto / Rm: 573382
