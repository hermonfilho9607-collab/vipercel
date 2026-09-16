# Prompts de imagem — Viper Cel

Os prompts estão em **inglês de propósito** — geradores de imagem (Midjourney,
DALL·E, Firefly, Stable Diffusion etc.) respondem melhor em inglês, mesmo
quando você vai usar a imagem num site em português. Copie exatamente como
está.

Todos seguem a mesma direção de luz da referência que você mandou (as
landing pages de carro escuras): fundo quase preto, **um** ponto de luz de
borda na cor da marca, produto nítido e o resto caindo pra escuridão. Se o
gerador aceitar, use a cor `#3358E8` (azul Viper Cel) como referência da luz.

---

## 1. Vitrine da loja — ✅ já resolvido com foto real

Você mandou uma foto real dos iPhones seminovos (`assets/seminovos.jpg`) e ela já
está no ar na seção Loja — escureci e apliquei uma vinheta pra combinar com o
resto do site. Não precisa gerar essa por IA. Prompt abaixo fica só como
referência, caso um dia vocês queiram uma segunda versão mais "produzida".

**Onde entra:** seção Loja, `assets/seminovos.jpg` — proporção 4:3.

```
Professional product photography of a stack of premium smartphones (iPhone-style),
arranged at a slight angle, on a dark reflective surface. Single dramatic rim light
in electric blue (#3358E8) tracing the edges of the phones from the upper right,
otherwise near-black background fading to pure black at the edges. Sharp focus on
the front phone's screen reflection, shallow depth of field on the phones behind it.
Studio product photography, cinematic automotive-ad lighting style, high contrast,
no text, no logos, no hands. 4:3 aspect ratio.
```

**Negativo (se o gerador aceitar):** `cluttered background, bright white background, multiple light sources, warm/orange lighting, text, watermark, logo`

---

## 2. Fundo do herói — opcional, mas é o que mais aproxima do estilo da referência

**Onde entra:** topo do site, atrás da logo. Ver instrução de código abaixo.

```
Cinematic product photography of a single modern smartphone floating at a slight
angle against a near-black background, dramatic rim lighting in electric blue
(#3358E8 to #6C8CFF) along the left edge of the phone, screen off or showing a
subtle blue glow. Wide empty dark space on the right two-thirds of the frame for
text overlay. Automotive-advertisement lighting style, high-end, moody, shallow
depth of field, very dark background with a soft blue glow gradient. No text, no
hands, no logos. 21:9 wide aspect ratio.
```

**Negativo:** `busy background, multiple objects, bright even lighting, warm tones, text, watermark`

**Como ativar depois de gerar (arquivo `assets/foto-heroi.jpg`):** abra
`assets/estilo.css`, ache a regra `.heroi-fundo` e adicione
`background-image: url('foto-heroi.jpg');` junto com `background-size: cover;
background-position: center;` — o gradiente que já existe continua servindo de
"moldura" nas bordas da foto.

---

## 3. Conserto em andamento — para a seção Serviços (opcional)

**Onde entra:** hoje a seção Serviços não tem foto (só ícones); essa imagem é
pra quando vocês quiserem adicionar uma.

```
Extreme close-up macro photography of hands using a precision screwdriver to
repair an open smartphone on a dark workbench, screen and internal components
visible. Dramatic single-source blue rim light (#3358E8) from the side, rest of
the frame falling into near-black shadow. Sharp focus on the tool and the phone's
internals, shallow depth of field blurring the hands slightly. Technical,
precise, premium repair-shop mood — not messy or cluttered. No visible face,
no logos, no text. 4:3 aspect ratio.
```

**Negativo:** `messy workbench, cluttered tools, bright lighting, visible face, logo, text, cheap-looking`

---

## 4. Imagem de compartilhamento (bônus — pra substituir a atual, gerada só com a logo)

**Onde entra:** `assets/compartilhamento.jpg`, 1200×630 — aparece quando alguém
manda o link do site no WhatsApp/Instagram.

```
Wide cinematic photograph of a premium smartphone against a near-black
background with a deep royal blue (#072E95) to electric blue (#3358E8)
gradient glow in the upper right corner, subtle grid/circuit-board texture
very faintly visible in the shadows. Large empty dark area on the left half
of the frame for a logo overlay. Automotive-advertisement mood, high-end,
cinematic. No text. 1200x630, landscape.
```

---

## Depois de gerar

1. Salve os arquivos com os nomes exatos indicados em cada seção (`foto-loja.jpg`, `foto-heroi.jpg`, etc.) dentro de `assets/`.
2. Comprima antes de subir se o arquivo passar de ~300-400KB (o site já reserva `loading="lazy"` pra imagens fora da primeira tela, mas arquivo pesado ainda deixa o carregamento inicial mais lento).
3. Me avisa que eu conecto cada imagem no lugar certo do código.
