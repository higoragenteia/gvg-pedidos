# GVG & ARTEFAL — PWA de Pedidos

Shell instalável que abre o **Aplicativo de Pedidos / Catálogo de Materiais** dentro do próprio app,
sem redirecionar para `script.google.com` e sem exibir a faixa azul do Google Apps Script.

## Arquitetura

```
GitHub Pages (shell + manifest + service worker + ícones)
        └── iframe em tela cheia → Apps Script /exec (app real)
```

O sistema, a planilha, os pedidos e a gestão continuam no Google Apps Script da conta da empresa.

## Links

- PWA: `https://higoragenteia.github.io/gvg-pedidos/`
- App (Apps Script): `https://script.google.com/macros/s/AKfycbzobPnorpwc2geTu-Tq37FwLfBtSb9knz3h_KsF6bx-yBtgwF-UKsY5_5vD-TyFZV9yMQ/exec`
- Planilha: `https://docs.google.com/spreadsheets/d/1tIy8EZpWKnD-tSl7cGMPX0cRBZwLIJYD6APD862ZKws/edit`

## Arquivos

- `index.html` — shell em tela cheia + iframe + instalação + instruções iOS/Android.
- `manifest.webmanifest` — nome, ícones, cores, `standalone`, `start_url` e `scope`.
- `sw.js` — service worker com versionamento de cache.
- `icone-180-pedidos-v3.png`, `icone-192-pedidos-v3.png`, `icone-512-pedidos-v3.png` — ícones do app.
- `.nojekyll` — necessário para GitHub Pages.

## Instalação

### Android

Abra a URL do GitHub Pages no Chrome e use **📲 Instalar** no canto inferior direito.

### iPhone

No Safari, abra a URL do GitHub Pages e use **Compartilhar → Adicionar à Tela de Início**.
O atalho permanece no GitHub Pages e abre o Apps Script no iframe, sem a faixa azul do Google.

Se o atalho antigo ainda mostrar o ícone anterior, apague-o da Tela de Início e adicione de novo,
pois o iOS mantém o ícone em cache. Os arquivos `icone-*-pedidos-v3.png` foram versionados para
forçar a troca.

> A implantação do Apps Script precisa estar como **Qualquer pessoa** (acesso anônimo) e o app
> usa o login próprio de usuário/senha. Assim o Google não abre a tela de login dentro do iframe.
> O catálogo é público; pedidos, histórico e gestão continuam exigindo login/aprovação.
> O link **Problemas para abrir? Toque aqui** só aparece após 15 segundos sem carregamento.

## Atualizações

O service worker usa `CACHE = 'gvg-pedidos-pwa-v3'`. Ao publicar uma nova versão do shell,
incremente esse valor. O conteúdo do Apps Script é atualizado pelo próprio Apps Script; os
funcionários não precisam reinstalar o PWA.
