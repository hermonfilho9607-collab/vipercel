# Viper Cel — manual do site

Site de uma página só (`index.html`), sem framework, sem build — HTML, CSS e um
pouco de JavaScript puro. Roda em qualquer hospedagem estática (o projeto já
está configurado para a Vercel).

---

## 1. O que falta antes de publicar

Três coisas ficaram em aberto porque dependiam de confirmação ou de material
que ainda não existia:

1. **Avaliação do Google.** Você mandou "4,957 avaliações no Google", mas isso
   quase certamente é a nota **4,9 ★** e a contagem **(57 avaliações)** coladas
   sem espaço/estrela ao copiar da ficha do Google. Não usei esse número em
   nenhum lugar do site — a seção de depoimentos usa só os 3 comentários reais
   que você mandou. Confirme o número certo e eu adiciono como um 4º dado de
   destaque (ao lado de "+10 anos" e "90 dias de garantia") e também no
   JSON-LD (dado estruturado que o Google lê).
2. **Redes sociais.** O rodapé só linka pro Google Maps (dado real). Manda o
   Instagram/Facebook se vocês tiverem, que eu adiciono.
3. **Fotografia real.** Ver seção 2 abaixo.

## 2. As fotos

Você pediu pra gerar as fotos com IA e anexar depois — os prompts prontos
foram entregues separadamente (mesma iluminação da referência: fundo quase
preto, luz de borda azul, produto em destaque).

Hoje:
- **Herói:** a logo (fundo removido) + a foto gerada por IA
  (`assets/foto-heroi.jpg`, um smartphone com luz de borda azul) posicionada
  à direita, atrás do conteúdo, com um degradê suave nas bordas esquerda e
  inferior pra não brigar com o texto. Some sozinha em telas estreitas
  (celular) — lá a logo e o texto já preenchem bem o espaço. Original em alta
  arquivado em `../fotos-originais/vipercel-hero-original.png`.
- **Seção Loja:** já tem a foto real que você mandou (`assets/seminovos.jpg`,
  os iPhones seminovos). Eu escureci e apliquei uma vinheta nela pra combinar
  com o resto do site (estava clara demais, fundo de madeira quente — destoava
  do azul/preto do site).

Pra qualquer foto nova que vocês adicionarem depois (ex: uma pro herói), o
padrão é: salve o arquivo em `assets/`, troque o conteúdo do elemento com a
classe correspondente por uma tag `<img src="assets/nome-do-arquivo.jpg"
alt="..." loading="lazy">`, mantendo a classe no elemento pai pra herdar a
moldura (arredondamento, sombra). Me chama que eu conecto — ou, se a foto vier
muito clara/quente pro estilo do site, eu ajusto (escurecer, vinheta) igual
fiz com a dos seminovos.

## 3. A marca (logo)

O arquivo `logo.jpg` que você mandou tinha um fundo azul sólido (sem
transparência) — funciona sobre o azul da própria logo, mas não sobre o fundo
quase-preto do site. Eu processei a imagem (removi o fundo por chroma-key e
"descontaminei" a borda pra não sobrar halo azulado) e gerei:

- `assets/logo.png` — logo completa (símbolo + "iper" + "assistência técnica
  especializada"), fundo transparente. Usada no herói.
- `assets/logo-icon.png` — só o símbolo da cobra, recortado e centralizado.
  Usada no cabeçalho, rodapé e como base dos favicons.
- `assets/favicon-16.png`, `favicon-32.png`, `apple-touch-icon.png` — ícone
  sobre fundo azul da marca (`#072E95`), pra ficar legível em aba de
  navegador clara ou escura.

Se um dia vocês tiverem a logo em vetor (AI/EPS/SVG) ou um PNG com
transparência de verdade, ela é mais nítida que essa versão recortada —
vale substituir.

## 4. Como o site foi construído

Direção de arte: **escura e cinematográfica**, baseada na sua própria logo
(azul `#072E95`) e nas duas referências que você mandou (landing pages
automotivas escuras — "Velocia Motors" e "Auto Reborn"). O racional completo
— paleta, tipografia, os porquês de cada decisão — está em
[`design-system/vipercel/MASTER.md`](design-system/vipercel/MASTER.md).

O conteúdo (endereço, telefone, horário, serviços, diferenciais, avaliações)
veio direto da sua ficha do Google Meu Negócio e das suas respostas — nada
foi inventado. Onde uma informação não estava confirmada (a avaliação do
Google, peças "originais" vs. "linha alternativa"), o texto foi escrito pra
refletir exatamente o que você confirmou, não o que soaria melhor.

## 5. Rodar no seu computador

Precisa de Python (já vem instalado no Windows/Mac na maioria dos casos).
Na pasta do projeto:

```bash
python -m http.server 5178
```

Depois abra `http://localhost:5178` no navegador. (Se você usa o Claude Code,
já existe um atalho configurado em `.claude/launch.json` — é só pedir pra
abrir o preview do "vipercel".)

## 6. Mapa dos arquivos

```
index.html              a página
404.html                 página de erro
assets/
  estilo.css              todo o CSS
  logo.png, logo-icon.png fotos e ícones (ver seção 3)
  favicon-*.png, apple-touch-icon.png
  compartilhamento.jpg    imagem de preview ao compartilhar o link (WhatsApp etc.)
robots.txt, sitemap.xml   SEO básico
vercel.json, _headers     cabeçalhos de segurança (Vercel e alternativas)
design-system/vipercel/   racional de design (não vai pro ar — ver .vercelignore)
```

---

**Antes de publicar de vez:** troque `vipercel.vercel.app` (aparece em
`index.html`, `sitemap.xml` e `robots.txt`) pelo domínio real, se vocês
usarem um domínio próprio em vez do subdomínio padrão da Vercel.
