# para-voce

Um pedido de namoro em uma página só. Cinco telas de enrolação, e o botão **NÃO** foge — no mouse e no dedo.

**[Ver funcionando →](https://fabiokoruja00.github.io/para-voce/)**

<!-- prints em docs/ quando houver -->

## O que é

Um arquivo HTML. Sem build, sem dependência, sem CDN, sem imagem externa. Abre no celular em 4G ruim e funciona.

A ideia veio de um reel do Instagram (`@devbyleobr`), mas o código é escrito do zero — não é fork nem cópia.

## Como funciona

Cinco telas antes da pergunta de verdade:

| # | tela | graça |
|---|---|---|
| 1 | "Você tá ocupada agora?" | as duas respostas levam adiante |
| 2 | grade com 9 coisas (🌙 🍓 🐶 🎸 🌊 🍀 🦋 ⭐ 🍫) | cada escolha tem uma resposta própria |
| 3 | "Escolhe um número" | 1, 2 ou 3 — todas erradas, de propósito |
| 4 | "Quanto você tá curiosa?" | slider que muda cara, frase, botão e tamanho do número |
| 5 | **a pergunta** | SIM leva à comemoração; NÃO foge para sempre |

Entre uma tela e outra entra a reação da escolha anterior, sozinha, por 3 segundos.

## Usar

Baixe o `index.html`, troque os textos e abra. É isso.

Para hospedar de graça: jogue o arquivo em qualquer repositório e ligue o GitHub Pages em **Settings → Pages → branch `main` / root**.

### O que dá pra mexer sem saber programar

Tudo no `index.html`:

- **as frases** — estão no HTML, em português claro
- **as 9 coisas da tela 2** — cada `<button>` tem o emoji e a resposta em `data-diz`
- **as caras do slider** — a lista `FAIXAS`, no script
- **quanto tempo a reação fica na tela** — `PAUSA_REACAO`, em milissegundos
- **as cores** — o `background` do `body` e o `--` do card

## As três armadilhas que esse tipo de página costuma cair

Se você for escrever a sua do zero, são estas que quebram:

**1. O botão que foge some no celular.** Se o card que contém o botão tem `transform` (qualquer animação de entrada), `position: fixed` deixa de valer contra a tela e passa a valer contra o card — o botão sai da área visível e não volta. Aqui o botão é movido para o `body` na primeira fuga.

**2. `innerHeight` mente no Chrome do Android.** Ele conta a faixa embaixo da barra de endereço, então o botão vai parar atrás dela. A conta certa usa `visualViewport`.

**3. Sem hover não há fuga.** No celular, `mouseover` nunca dispara — o "NÃO" vira um botão comum e clicável. Precisa de `touchstart` com `preventDefault`.

## Licença

MIT — use, mude, publique. Se der certo com alguém, a gente aceita o convite do casamento.
