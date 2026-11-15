 (`index.html`, `exposicoes.html` e `cadastro.html`).
Os arquivos `styles.css`, `dados.js` e `script.js` ja estao linkados nas paginas.

## dados.js

```js
window.OBRAS_VITRINE = [
  {
    id: "obra-01",
    categoria: "concreta", //filtro: concreta, acervo, casarao ou saraus
    categoriaLabel: "Exposição Atual",
    codigo: "EM CARTAZ • 12/11 A 13/12/2026",
    titulo: "20 Mil Léguas Submarinas e outras viagens extraordinárias",
    resumo: "Mostra temporária e interativa em cartaz no museu.",
    imagem: "assets/images/oficial/cr-exposicao-atual.webp",
    alt: "Cartaz oficial da exposição na Casa das Rosas",
    credito: "casadasrosas.org.br • Em Cartaz",
    direitos: "Divulgação institucional autorizada",
    visita: "Salas expositivas • Entrada gratuita",
    destaqueHome: true,      // pra aparecer nos 3 cards da home
    destaqueSpotlight: true, // pra aparecer no destaque no topo de exposicoes.html
    ficha: {
      tag: "Em Cartaz • 12/11 a 13/12/2026",
      descricao: "Descrição completa que abre no modal.",
      audio: "Audiodescrição de abertura (2min 10s).",
      direitosCompletos: "Material oficial da Casa das Rosas / Poiesis."
    }
  }
];
```

## script.js

No topo das páginas:
- `#fonte-diminuir`, `#fonte-aumentar` e `#alto-contraste` (o alto contraste é `data-contrast="high"` )
- `.btn-menu` abre menu `#navegacao-principal` com
 a classe `.is-open`

Na `index.html`:
- `#vitrine-home-grade` recebe os clones do `#tpl-obra-home`
- Abas da linha do tempo usam `data-epoca` e mostram o painel com o mesmo `data-painel-epoca` (tira `.is-hidden` e coloca `.is-active` na aba)

pagina `exposicoes.html`:
- `#grade-exposicoes` recebe `#tpl-exposicao` (campos: `imagem`, `status`, `periodo`, `local`, `titulo`, `resumo` e atributo `data-selecionar-exposicao` com a categoria da exposicao)
- Ao clicar em `[data-selecionar-exposicao]`, rola ate `#secao-obras-exposicao` e aplica o filtro (`#btn-voltar-exposicoes` volta pra `#secao-exposicoes`)
- Mapa interativo `#mapa-exposicoes`: zonas clicaveis do SVG (`.mapa-zona[data-sala]`) e botoes `[data-sala]` atualizam `.is-active`, `#mapa-sala-etiqueta`, `#mapa-sala-titulo`, `#mapa-sala-descricao` e o `data-selecionar-exposicao` do `#mapa-sala-link`
- `#vitrine-destaque` recebe `#tpl-obra-destaque`
- `#grade-obras` recebe `#tpl-obra-vitrine`
- Campo `#busca-exposicoes`, botoes `[data-filtro]` e texto `#contagem-obras`
- Cards clicaveis (`.card-clicavel` com `.card-acao-link`) e gatilhos `[data-abrir-obra]` abrem o `<dialog id="modal-curatorial">` e preenchem `#modal-etiqueta`, `#modal-titulo`, `#modal-imagem`, `#modal-descricao`, `#modal-som` e `#modal-direitos` (`#btn-audioguia` toca a narracao via `speechSynthesis` com status no `#audioguia-status`; `#modal-fechar` fecha e para o audio)

pagina `cadastro.html`:
- Formulario `#formulario-visitante` com `#nome-visitante`, `#email-visitante`, `#aceita-notificacoes` e div `#retorno-formulario`

## Css 

- Classes estado usadas pelo js: `.is-active`, `.is-open` e `.is-hidden`.
- classes principais (`.barra-topo`, `.cabecalho`, `.secao`, `.card-obra`, `.card-clicavel`, `.card-acao-link`, `.mapa-grade`, `.mapa-planta`, `.mapa-svg`, `.mapa-zona`, `.mapa-botoes`, `.modal-audio-cabecalho`, `.modal-audio-status`, `.cartao-formulario`, `.rodape`, `.container`, `.hero`, `.btn`, `.card`, `.grid-2`, `.grid-3`).
