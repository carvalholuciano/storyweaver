# StoryWeaver

[![Built with pollinations.ai](https://img.shields.io/badge/Built%20with-Pollinations-8a2be2?style=for-the-badge&logoColor=white&labelColor=6a0dad)](https://pollinations.ai)

Ilustrador de histórias com IA. Você escreve uma ideia e o app cria um miniconto ilustrado, cena por cena: o texto é escrito pela API de texto da Pollinations e cada parágrafo é ilustrado pela API de imagem.

Página única em HTML, CSS e JavaScript, sem backend.

## Funcionalidades

- História em português a partir de uma ideia livre
- Ilustração para cada cena, com seis estilos de arte
- Número de cenas ajustável (3, 4 ou 5)
- Sugestões de ideias
- Salvar ou imprimir a história

## Autenticação

O app funciona em dois modos:

- **Anônimo** (padrão): usa os endpoints públicos `text.pollinations.ai` e `image.pollinations.ai` com o `referrer`. Não exige login, mas tem limites baixos e pode retornar erro 429 ("fila cheia") em rede compartilhada.
- **Conectado (BYOP — Bring Your Own Pollen)**: o visitante clica em "Conectar Pollinations", autoriza com a conta dele e o app passa a gerar usando o saldo de pollen do próprio usuário, via `gen.pollinations.ai` com `Authorization: Bearer`. Sem fila compartilhada e sem custo para o desenvolvedor.

### Chave publicável (`pk_`)

Para que o app apareça com nome próprio na tela de autorização e o tráfego seja atribuído à sua conta (o que conta para subir de tier):

1. Em `enter.pollinations.ai`, crie uma **App Key** publicável (`pk_...`).
2. Cadastre o **Redirect URI** exato do app, ex.: `https://carvalholuciano.github.io/storyweaver/`.
3. Cole a chave na constante `APP_PUBLISHABLE_KEY` no `index.html`.

A `pk_` pode ficar no código do frontend com segurança — é o que ela foi feita para ser. A chave secreta (`sk_`) **nunca** deve ir para o frontend.

## Configuração

No início do `<script>` em `index.html`:

- `APP_REFERRER` — domínio enviado nas chamadas anônimas
- `APP_PUBLISHABLE_KEY` — sua chave `pk_` (opcional, para atribuição/BYOP)
- `TEXT_MODEL` — modelo de texto (`openai`)
- `IMG_MODEL` — modelo de imagem (`flux`)

## Tecnologia

- Anônimo: `text.pollinations.ai` e `image.pollinations.ai`
- Conectado: `gen.pollinations.ai` (`/v1/chat/completions` e `/image/{prompt}`)
- Autorização BYOP: `enter.pollinations.ai/authorize`

## Créditos

Construído com a [pollinations.ai](https://pollinations.ai) — plataforma open-source de IA generativa que fornece o texto e as imagens.

- Logos oficiais: [pollinations.ai Logo White](https://raw.githubusercontent.com/pollinations/pollinations/main/assets/logo.svg) · [pollinations.ai Logo Text White](https://raw.githubusercontent.com/pollinations/pollinations/main/assets/logo-text.svg)
- Badge: [Built With pollinations.ai](https://pollinations.ai)

## Licença

MIT.
