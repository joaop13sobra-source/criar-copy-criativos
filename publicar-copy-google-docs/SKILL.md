---
name: publicar-copy-google-docs
description: Publica copy de criativos estáticos (headline + copy + CTA + direção de arte + legenda) ou roteiros já aprovados num Google Docs formatado de verdade (heading, negrito e listas reais, não markdown cru), seguindo o template validado na conta AeroTD. Sempre termina com releitura obrigatória do documento publicado pra pegar erro ortográfico, de concordância, registro pra/para e coerência com a premissa do negócio antes de entregar o link. Use depois que a copy já foi escrita/aprovada (ex: pela `/criar-copy-criativos`) e o usuário pedir pra subir isso num Google Docs.
user-invocable: true
---

# /publicar-copy-google-docs — Subir copy de criativos estáticos pro Google Docs formatado

Pega um roteiro, uma transcrição de call, ou uma copy de criativos estáticos já escrita (headline + copy + CTA + direção de arte + legenda) e publica num Google Docs formatado — heading real (H1/H2/H3), negrito real, listas reais — no layout validado na conta AeroTD (criativos "Ainda dá tempo", 22/09/2026). Sempre termina com uma rodada de revisão ortográfica pós-publicação, porque essa etapa faltou nas primeiras vezes que essa skill foi usada manualmente e gerou 6 retrabalhos seguidos no mesmo doc.

## Quando usar
- Depois que a `/criar-copy-criativos` já gerou/aprovou o conteúdo (headline, copy, CTA, direção de arte, legenda de anúncio, ou roteiro de vídeo) e o usuário pede pra subir isso num Google Docs.
- Serve tanto pra vertente "criativo estático" quanto "roteiro de vídeo" da `/criar-copy-criativos` — mesma lógica de documento, campos adaptados (Gancho/Corpo/CTA/Direção de cena/Legenda no lugar de Headline/Copy/CTA/Direção de arte/Legenda).
- Não usar pra criar o conteúdo do zero — isso é trabalho da `/criar-copy-criativos`. Esta skill só cuida da publicação formatada.

## A armadilha técnica (por que isso existe)
`mcp__claude_ai_Google_Drive__create_file` com `contentMimeType: "text/plain"` **não interpreta markdown**. Se você mandar texto com `#`, `##`, `**negrito**`, esses caracteres entram literalmente no documento como texto puro — sem virar heading, sem virar negrito. Isso já aconteceu nesta conta (primeira subida do doc de copy da AeroTD saiu com `#` e `**` literais na tela).

**A solução é subir como HTML.** `contentMimeType: "text/html"` com tags reais (`<h1>`, `<h2>`, `<h3>`, `<strong>`, `<ul>`, `<ol>`, `<hr>`, `<p>`, `<br>`) é convertido pelo Google Drive em formatação real de Google Docs — heading de verdade, negrito de verdade, lista de verdade.

Não existe ferramenta de "editar conteúdo de um Google Doc existente" nesse conector (`update_file` só mexe em título/pasta, nunca em conteúdo). Pra corrigir um doc já publicado: `create_file` de novo com o mesmo título (gera um arquivo novo, com ID novo) e depois `trash_file` no ID antigo. Sempre nessa ordem — cria o novo, confirma que subiu, só então joga o antigo pro lixo.

## Como confirmar que a formatação pegou
Depois de publicar, leia o arquivo de volta com `mcp__claude_ai_Google_Drive__read_file_content`. Essa ferramenta devolve uma representação em markdown do documento *real* — ou seja, se a formatação pegou, um H1 real vira `# **Texto**` no retorno, um H2 vira `## **Texto**`, uma lista numerada vira `1.  Item`. Se em vez disso aparecer o texto cru sem essa notação, a formatação não pegou (geralmente sinal de que foi subido como `text/plain` por engano).

Não confundir isso com erro: emoji às vezes volta corrompido nessa leitura (ex: 📲 aparece como `ð²`). Isso é um artefato de encoding da ferramenta de leitura, não um defeito real do documento — não "corrigir" removendo o emoji por causa disso. Se tiver dúvida, abra o `viewUrl` do documento e olhe visualmente.

## Estrutura do documento (template validado)

```html
<h1>TÍTULO DA PEÇA (maiúsculo, ex: CRIATIVOS ESTÁTICOS DE REMARKETING)</h1>
<h2>"Subtítulo/conceito da campanha" | detalhe</h2>

<p><strong>Cliente:</strong> Nome<br>
<strong>Origem:</strong> de onde saiu o brief (call, briefing, etc.), com data</p>

<hr>

<h1>1. PREMISSAS GERAIS</h1>
<ul>
<li>Público, contexto do porquê dessa campanha existe.</li>
<li>Guardrails do cliente (do-e-dont): o que não pode ser dito/mostrado.</li>
<li>Regras de formato (ex: toda peça tem legenda de anúncio, não frase única).</li>
</ul>

<hr>

<h1>CRIATIVOS DO CLIENTE | NOME DA FRENTE</h1>
<p><strong>Quantidade:</strong> N criativos<br>
<strong>Formato:</strong> onde clica, pra onde vai.</p>

<h3>Conceito visual geral</h3>
<p>O que a imagem precisa comunicar em todas as peças, uma vez só (não repetir por peça).</p>
<p><strong>Importante:</strong> o que evitar visualmente.</p>

<hr>

<h2>CRIATIVO 1: NOME DO ÂNGULO</h2>
<p><strong>Nível de funil:</strong> Topo/Meio/Fundo</p>

<h3>Headline</h3>
<p>"Texto do hook"</p>

<h3>Copy</h3>
<p>Linha 1.<br>
Linha 2.<br>
Linha 3 (se houver instrução de clique).</p>

<h3>CTA</h3>
<p>"Texto do botão →"</p>

<h3>Direção de arte</h3>
<ol>
<li>O que muda desse criativo em relação ao conceito visual geral.</li>
</ol>

<h3>Legenda do post (Meta Ads)</h3>
<p>Gancho.<br>
1-2 frases de corpo reforçando a mensagem.<br>
Linha de CTA com emoji. 📲</p>

<hr>

<!-- repetir bloco CRIATIVO N por peça -->

<h1>RESUMO DOS CRIATIVOS</h1>
<h2>Cliente | Nome da frente</h2>
<ol>
<li><strong>Nome do ângulo 1</strong> (nível de funil)</li>
</ol>

<hr>

<p><strong>Referência completa:</strong> caminho do arquivo fonte (transcrição, briefing).</p>
```

Pra vertente "roteiro de vídeo" da `/criar-copy-criativos`, trocar os campos por criativo assim (mantendo o resto do template igual): `Headline` → `Gancho`, `Copy` → `Roteiro — Fala`, `Direção de arte` → `Direção de cena` (lista numerada de passos de filmagem/edição). `CTA` continua `CTA` (marcar como "CTA — Falado" se for roteiro).

Regras de montagem:
- `<hr>` sempre entre blocos principais (premissas, seção de criativos, cada criativo, resumo).
- Quando várias peças compartilham o mesmo conceito visual, escrever "Conceito visual geral" uma vez só (fora dos blocos de criativo) e, por peça, só a "Direção de arte"/"Direção de cena" com a variação específica — nunca repetir a descrição inteira peça a peça.
- Nome do arquivo/título do Google Doc: `<Cliente> - Copy Criativos - <Nome da frente> - <AAAA-MM-DD>` (ou `<Cliente> - Roteiros de Vídeo - <Nome da frente> - <AAAA-MM-DD>` pra vertente vídeo).
- Publicar na pasta central do cliente no Drive (`<cliente>/links.md` tem o ID) — nunca solto na raiz do Drive.

## Regras de copy a aplicar antes de publicar (consolidado de correções reais, 22/09/2026)

Essas não são regras que essa skill inventa — são erros que passaram batido em rodadas anteriores e só foram pegos porque o usuário revisou manualmente. Aplicar **antes** de subir, não depois:

1. **Sem travessão (—) em nenhum campo.** Trocar por ponto final, vírgula ou dois-pontos. Isso vale pra headline, copy, legenda, premissas — documento inteiro, não só onde foi citado.
2. **Registro consistente de "para".** Não misturar "pra" e "para" no mesmo documento sem critério. Definir um registro (formal "para" ou informal "pra") e aplicar em todo o texto, incluindo "pro" → "para o" se for pro lado formal.
3. **Conjugação de imperativo consistente.** Se a peça fala com "você", todo verbo no imperativo tem que estar na forma de "você" (fale, clique, volte, resolva, garanta, não deixe) — nunca misturar com a forma de "tu" (fala, clica, volta, resolve, não deixa). Erro real que aconteceu: "Fale... e resolve isso" (mistura "fale"/você com "resolve"/tu) e "Não deixa..." (deveria ser "Não deixe", imperativo negativo correto).
4. **Concordância de gênero do pronome com o substantivo real.** Antes de escrever "ele"/"ela", "reservado"/"reservada", confirmar a que substantivo o pronome se refere de fato (ex: "vaga" e "matrícula" são femininas; "lugar" é masculino — não dá pra falar de "vaga" na frase anterior e usar "ele" depois).
5. **Coerência entre a copy e a situação real do lead/premissa do negócio.** Não afirmar como fato algo que as premissas contradizem (ex: dizer "você já garantiu sua vaga" ou "vaga reservada" quando a premissa é que o lead nem pagou o boleto ainda — isso é uma promessa falsa, não só um erro de estilo). Também não inventar mecanismo que não foi confirmado pelo cliente (ex: "fila de espera" sem confirmação de que existe).
6. **Legenda de anúncio Meta Ads é sempre multi-linha** (gancho + 1-2 frases de corpo + linha de CTA com emoji), nunca uma frase solta — mesmo que a copy do criativo em si seja curta.
7. **Aplicar os guardrails do cliente** (arquivo `do-e-dont.md` ou equivalente na KB do cliente) antes de fechar qualquer headline/copy — nomes proibidos, claims não comprováveis, tom institucional demais, etc.

## Passo a passo

1. Reunir o conteúdo já aprovado (headline/copy/CTA/direção de arte/legenda por peça, ou roteiro completo).
2. Checar os 7 pontos da seção acima nesse conteúdo **antes** de montar o HTML — não confiar que quem escreveu já aplicou tudo.
3. Montar o HTML seguindo o template da seção "Estrutura do documento".
4. Descobrir a pasta central do cliente no Drive (`<cliente>/links.md`) e o título do arquivo.
5. Publicar com `mcp__claude_ai_Google_Drive__create_file`, `contentMimeType: "text/html"`.
6. **Obrigatório, não pular:** ler o arquivo de volta com `read_file_content` e revisar linha por linha:
   - Formatação pegou (heading/negrito/lista aparecem como markdown real na leitura, não como texto cru com `#`/`**` literais)?
   - Ortografia e acentuação corretas?
   - Os 7 pontos de copy da seção anterior, aplicados em 100% do texto (não só na peça que alguém revisou por último)?
   - Alguma promessa/afirmação que não bate com as premissas do negócio?
7. Se achar qualquer problema no passo 6: corrigir o HTML, publicar de novo (novo `create_file`, mesmo título), confirmar que a nova versão está certa, **só então** jogar a versão anterior pro lixo (`trash_file`).
8. Entregar o link (`viewUrl` do resultado do `create_file`) pro usuário. Nunca declarar "pronto" sem ter passado pelo passo 6.

## Referência real
Documento validado como modelo de formatação: "AeroTD - Copy Criativos - Remarketing Ainda Dá Tempo - 2026-09-22" (conta AeroTD, pasta central do Drive do cliente). Passou por 6 rodadas de correção nesta mesma conversa (travessão, registro pra/para, concordância de gênero, coerência com a premissa de negócio) antes de ficar limpo — é exatamente o tipo de erro que o passo 6 desta skill existe pra pegar na primeira tentativa.
