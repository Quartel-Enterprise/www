# Quare Software Landing Page

Landing page da Quare Software construída com Astro, TypeScript e Tailwind CSS. O projeto usa renderização sob demanda no servidor com o adaptador Node em modo standalone.

## Requisitos

- Node.js 22.12 ou superior (Node 24 recomendado)
- npm 11 ou superior

## Desenvolvimento

```bash
npm install
npm run dev
```

O servidor de desenvolvimento abre em `http://localhost:4321`.

## Verificação e build

```bash
npm run check
npm run build
npm start
```

O comando `build` executa a análise estática do Astro e gera o servidor em `dist/server/entry.mjs`. O comando `start` executa esse artefato em produção.

## Estrutura

```text
src/
├── components/   Componentes visuais e interações progressivas
├── layouts/      Documento HTML, metadados e estilos globais
├── pages/        Rotas renderizadas pelo Astro
└── styles/       Design tokens e base do Tailwind
```

A página entrega todo o conteúdo no HTML inicial. O JavaScript no cliente é usado para o shader WebGL progressivo do hero, o acordeão de produtos, as prévias interativas e o diálogo de detalhes. Navegadores sem WebGL recebem automaticamente a atmosfera em CSS.
