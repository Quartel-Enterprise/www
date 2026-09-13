# AGENTS.md

## Estratégia de renderização

Este projeto é uma landing page inteiramente estática. Preserve o prerender como estratégia padrão para que o build produza HTML, CSS e JavaScript distribuíveis diretamente por CDN, com menor latência e sem custo de renderização por requisição.

- Mantenha `output: 'static'` em `astro.config.ts`.
- Mantenha `export const prerender = true` nas páginas estáticas, mesmo sendo o comportamento padrão, para tornar a decisão explícita.
- Não adicione um adaptador de servidor enquanto todas as rotas puderem ser resolvidas durante o build.
- WebGL, interações no DOM, consentimento de cookies e analytics executados no cliente são compatíveis com prerender e não justificam desativá-lo.

## Quando reavaliar o prerender

Reavalie esta decisão quando o HTML ou a resposta HTTP precisar depender da requisição, por exemplo:

- personalização baseada em cookies, sessão ou identidade;
- autenticação ou conteúdo específico do usuário;
- atribuição de experimentos A/B realizada no servidor;
- geolocalização, cabeçalhos ou parâmetros processados no servidor;
- dados que precisam ser consultados em tempo de requisição;
- endpoints próprios para coleta ou processamento de analytics.

Analytics apenas no navegador ou uma faixa de consentimento de cookies não tornam a página dinâmica. Um endpoint de analytics também pode ser dinâmico sem alterar o prerender da landing page.

Se a renderização sob demanda se tornar necessária:

1. documente qual requisito depende da requisição;
2. escolha o adaptador compatível com o provedor de hospedagem;
3. defina `export const prerender = false` somente nas rotas afetadas;
4. mantenha as demais páginas prerenderizadas;
5. defina a política de cache e invalidação do CDN;
6. valide o comportamento sem JavaScript e o conteúdo entregue no HTML inicial.
