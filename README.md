# Site Modelo Institucional Completo

Template de site institucional "completo" (várias seções, estilo site profissional), feito em [Hugo](https://gohugo.io/), pronto para publicar grátis no Cloudflare (Workers com arquivos estáticos) e editar pelo [Pages CMS](https://pagescms.org/).

Diferente do `site-modelo-institucional` (formato link-na-bio), esse aqui é uma página única mais longa e "vendedora", com cabeçalho fixo, seção de destaque (hero), quem somos, serviços, produtos/vitrine opcional, blog/notícias opcional, mapa de localização e rodapé completo. Sem carrinho de compras — para isso existe o `site-modelo-catalogo-completo`.

## Seções da página

1. **Cabeçalho fixo** — logo, nome, menu com âncoras, botão de WhatsApp
2. **Hero** — selo, título com destaque colorido, descrição, dois botões, foto
3. **Quem Somos** — fotos, texto e 3+ selos de credibilidade (lista editável)
4. **Serviços** — grade de cards (ícone, título, descrição, botão opcional) — quantos você quiser
5. **Produtos/Vitrine** *(opcional, liga/desliga)* — cards com foto e botão de WhatsApp por item, sem carrinho
6. **Faixa de aviso** *(opcional, liga/desliga)* — texto rolante
7. **Blog/Notícias** *(opcional, liga/desliga)* — só aparece se tiver post publicado
8. **Localização** — mapa do Google incorporado (gerado a partir do endereço, sem precisar de chave de API) + botão "Como Chegar"
9. **Rodapé** — logo, links rápidos, contato, redes sociais, copyright automático
10. **Botão flutuante de WhatsApp**

## Como usar este template para um novo cliente

1. Crie um novo repositório a partir deste
2. No Cloudflare, crie um projeto do tipo **Worker** conectado ao repositório:
   - **Comando da build**: `hugo --minify`
   - **Comando de implantação**: `npx wrangler deploy`
   - **Diretório raiz**: `/`
3. Configure o [Pages CMS](https://pagescms.org/) apontando pro repositório — o `.pages.yml` já define todos os campos
4. Edite `content/_index.md` e as coleções (`selos`, `servicos`, `vitrine`, `blog`) com as informações reais do cliente
5. Ligue "Produtos" e/ou "Blog" no perfil só se o cliente for usar essas seções

## Estrutura

```
content/
  _index.md    → perfil + textos de todas as seções fixas
  selos/       → selos de credibilidade (Quem Somos)
  servicos/    → cards de serviços
  vitrine/     → cards de produtos/categorias (seção opcional)
  blog/        → posts do blog/notícias (seção opcional)
layouts/
  index.html          → monta a página inteira, seção por seção
  blog/list.html       → lista de posts
  blog/single.html      → post individual
  partials/
    header.html, footer.html, theme-style.html, analytics.html
static/
  css/style.css  → todo o visual do site
  js/main.js     → menu mobile
  img/           → logo, fotos, fundo
```

## Desenvolvimento local

Requer [Hugo](https://gohugo.io/installation/) instalado.

```
hugo server -D
```
