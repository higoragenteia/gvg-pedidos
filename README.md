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
- `icone-180.png`, `icone-192.png`, `icone-512.png` — ícones do Almoxarifado.
- `.nojekyll` — necessário para GitHub Pages.

## Instalação

### Android

Abra a URL do GitHub Pages no Chrome e use **📲 Instalar** no canto inferior direito.

### iPhone

No Safari, abra a URL do GitHub Pages e use **Compartilhar → Adicionar à Tela de Início**.

> Se o Safari bloquear o login dentro do iframe, use o link
> **Problemas para abrir? Toque aqui** no canto inferior esquerdo.

## Atualizações

O service worker usa `CACHE = 'gvg-pedidos-pwa-v1'`. Ao publicar uma nova versão do shell,
incremente esse valor. O conteúdo do Apps Script é atualizado pelo próprio Apps Script; os
funcionários não precisam reinstalar o PWA.
