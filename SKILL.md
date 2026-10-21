---
name: criar-copy-criativos
description: Gera copy de anúncio pra qualquer cliente, em duas vertentes — "criativo estático" (headline + copy + CTA + direção de arte) e "roteiro de vídeo" (gancho + corpo + CTA) — sempre ancorada num ângulo da Biblioteca de Ângulos de Copy (78 ângulos em 5 categorias, organizadas por nível de consciência) e no contexto real do projeto/cliente. Pergunta a vertente, depois pra qual projeto é a copy, puxa o contexto desse projeto (CLAUDE.md, DCC, UCM, ou skill dedicada `criar-copy-<cliente>` se existir), sugere ângulos da biblioteca com base nesse contexto, e só escreve a copy depois que o usuário escolhe o ângulo. Aplica por cima o guardrail de copy enxuta da Colli&Co e a estrutura de elementos de persuasão (benefício, quebra de objeção, credibilidade, mecanismo, gatilhos mentais). Use quando pedir pra "brifar/escrever criativo estático", "roteiro de vídeo", "copy de anúncio", "headline + copy + CTA", "gancho corpo CTA", ou "sugere ângulos" de qualquer cliente que NÃO tenha uma skill própria mais específica.
user-invocable: true
---

# /criar-copy-criativos — Copy de anúncio (estático ou roteiro), ancorada em ângulo

Gera copy de anúncio pra qualquer cliente, partindo sempre de um ângulo escolhido junto com o usuário na Biblioteca de Ângulos de Copy, com o contexto real do projeto por baixo e o guardrail de copy enxuta da Colli&Co por cima. Não é hardcoded pra um cliente — descobre o contexto dinamicamente a cada chamada.

Todo o material de referência (transcrições, frameworks, planilha exportada) está em `skills-gerais/criar-copy-criativos/Gerador de anúncios/`.

Depois que a copy estiver escrita/aprovada, se o usuário pedir pra subir num Google Docs formatado, usar a sub-skill `publicar-copy-google-docs/SKILL.md` (nesta mesma pasta) — template de formatação validado (HTML real, não markdown cru), regras de revisão ortográfica/gramatical consolidadas de correções reais, e releitura obrigatória do documento publicado antes de entregar o link.

## Duas vertentes

A skill sempre produz uma das duas — perguntar qual, nunca presumir:

- **Criativo estático** — headline + copy + CTA + direção de arte (peça parada: KV, anúncio Meta/Google, banner).
- **Roteiro de vídeo** — gancho + corpo + CTA (peça em vídeo: Reels, anúncio em vídeo, VSL curta).

## Fluxo (nessa ordem, sempre)

1. **Perguntar a vertente**: criativo estático ou roteiro de vídeo.
2. **Perguntar para qual projeto** é a copy.
3. **Puxar o contexto desse projeto** (ver "Passo 0" abaixo).
4. **Levantar o mini-briefing** (ver seção própria) — a partir do contexto puxado, completando com o usuário só o que faltar. Se o projeto tiver mais de uma frente/produto/persona/marca, ou o nível de funil não for óbvio pelo pedido, **perguntar via pergunta estruturada de múltipla escolha** (ver "Como perguntar" abaixo) — não assumir.
5. **Sugerir ângulos** da Biblioteca de Ângulos com base no contexto + briefing + nível de funil (ver "Sugerindo ângulos"), **sempre via pergunta estruturada de múltipla escolha**.
6. **Usuário escolhe o ângulo** (ou pede pra ver mais opções/outra categoria).
7. **Escrever a copy** a partir do ângulo escolhido, no formato da vertente e no template fixo de saída (ver "Escrevendo a copy" e "Saída — formato por peça").

Nunca pular direto pro rascunho sem ter passado pelos passos 1-6 — a copy nasce do ângulo escolhido pelo usuário, não de uma suposição.

### Como perguntar (passos 1, 4 e 5 — decisões de direção, antes de escrever)

Usar a ferramenta de pergunta estruturada de múltipla escolha (não texto livre) pra:
- Vertente (estático/roteiro).
- Frente de produto / persona / marca específica, quando o projeto tiver mais de uma (ex.: 3 frentes de anúncio, 2 sub-marcas, personas por momento de busca).
- Nível de funil (topo/meio/fundo), com 1 opção marcada como recomendada e o porquê, quando o contexto já sugerir uma direção.
- Candidatos de ângulo da Biblioteca (3-4 opções), cada uma com o nome do ângulo + 1-2 linhas explicando por que aquele ângulo encaixa nesse projeto/persona específico — nunca só colar a explicação genérica da planilha.

Isso é diferente do "Padrão de iteração" (mais abaixo), que rege ajuste de texto **já escrito** — ali a regra é o oposto: nunca usar pergunta estruturada, listar variações em texto simples. Pergunta estruturada é só pras decisões de direção **antes** de escrever a peça.

## Passo 0 — descobrir o contexto do projeto

Depois de saber qual projeto, checar nessa ordem (parar na primeira que existir):
1. `<cliente>/skills/criar-copy-<cliente>/SKILL.md` — se existir, **usar ela em vez desta pra tom/regras/exemplos**, mas o fluxo de ângulo (passos 1-6 acima) continua valendo por cima.
2. `<cliente>/contexto-do-projeto/` — base de conhecimento condensada (posicionamento, persona, regras do que não fazer).
3. `<cliente>/dcc/` (Documento de Concepção de Copywriting) e `<cliente>/ucm/` (Use Case Map) — CVBA, pilares de marca, personas, dores/objeções, headlines de referência.
4. `<cliente>/CLAUDE.md` — contexto geral (negócio, tom de voz, riscos, regras).
5. Se nada disso existir: consultar NotebookLM do cliente (`/notebooklm-consulta-cliente`) ou perguntar o mínimo ao usuário.

Nunca inventar pilar de marca, persona ou regra de proibição que não esteja em nenhuma dessas fontes — marcar como "não validado" se for elaboração própria a partir do material disponível.

Se já vier um briefing pronto no formato padrão do `/ekyte-briefing` (siglas KV/CA, salvo em `<cliente>/produtos/<Produto>/outputs/<AAAA-MM>/briefings/`), usar ele como fonte primária — Persona, Estratégia Central (Deve/Não deve) e Design já vêm prontos de lá, sem precisar re-perguntar.

## Mini-briefing (antes de sugerir ângulo)

Levantar, priorizando o que já existe no contexto do Passo 0 e perguntando ao usuário só o que faltar:

- **Argumentos de credibilidade** — por que o cliente/produto merece confiança (história, autoridade, números, bastidores).
- **Argumentos de promessa/benefício** — funcional (o benefício óbvio), dimensional (a consequência prática dele na vida real) e emocional (a consequência emocional). Ex.: ganhar mais dinheiro (funcional) → poder viajar (dimensional) → ficar tranquilo (emocional).
- **Quebras de objeção** — as 5 objeções universais (tempo, dinheiro, esforço, conhecimento, risco) e a resposta de cada uma pro produto em questão. Exceção: se o produto exige algo de verdade (ex.: é caro), pode virar **filtro** proposital em vez de objeção a esconder.
- **CTAs possíveis**, alinhados à oferta real.
- **Público** — dores (o que incomoda/frustra) e desejos (o que quer alcançar/sentir/se tornar).
- **Nível de funil**: perguntar explicitamente qual — **topo** (nunca ouviu falar), **meio** (já conhece, ainda avaliando), **fundo** (já é cliente/confia). Usar pra filtrar categoria de ângulo (ver tabela abaixo).

Regra prática: se na hora de escrever sentir falta de um argumento, o briefing tá incompleto — voltar e completar, não inventar.

**Diretriz específica do cliente vs. guardrail genérico desta skill**: se o contexto do Passo 0 (CLAUDE.md, check-ins, skill dedicada) trouxer uma regra explícita e validada que conflita com um padrão desta skill (ex.: "não mencionar a solução no topo de funil" vs. a regra de "benefício sempre obrigatório"), a diretriz específica do cliente vence — mas o desvio precisa ser **sinalizado explicitamente na entrega** (nota de execução separada, nunca silencioso), explicando qual regra genérica foi deixada de lado e por quê.

## A Biblioteca de Ângulos de Copy

Fonte: planilha "Biblioteca de Ângulos de Copy para Anúncios" (Google Sheets, acesso via Service Account — ver `skills-gerais/google-sheets-write-access.md`), já exportada em CSV em `Gerador de anúncios/biblioteca-angulos_<Categoria>.csv` (Problema, Solução, Produto, Oferta, Genéricos — 78 ângulos, colunas `# | Ângulo | Explicação | Exemplo | Prompt`). Ler os CSVs locais por padrão; se o usuário disser que atualizou a planilha, reexportar via Service Account antes de usar.

Ângulo é o **ponto de vista central** do anúncio — não é gatilho mental, não é formato. Formato (caixinha de pergunta, entrevista na rua etc.) é reaproveitável em qualquer ângulo; aqui a skill não gerencia biblioteca de formatos, só ângulo + estrutura.

### Categorias × nível de consciência × nível de funil

| Categoria | Nível de consciência (Eugene Schwartz) | Nível de funil desta skill |
|---|---|---|
| **Problema** (20 ângulos) | 1. Inconsciente / 2. Consciente do problema | Topo |
| **Solução** (18 ângulos) | 3. Consciente da solução | Meio |
| **Produto** (15 ângulos) | 4. Consciente do produto | Meio/Fundo |
| **Oferta** (16 ângulos) | 5. Totalmente consciente | Fundo |
| **Genéricos** (9 ângulos) | Todos — atravessam qualquer categoria (curiosidade, polêmica, desafio, psicologia reversa, analogia) | Qualquer um |

- **Problema** — fala só da dor, sem mencionar solução ainda.
- **Solução** — já pressupõe consciência do problema; mecanismo, novidade, comparação de métodos, atalho, simplicidade — sem vender o produto especificamente ainda.
- **Produto** — prova social, especificidade, estudo de caso, depoimento.
- **Oferta** — o anúncio inteiro gira em torno de UM eixo tipo gatilho mental sustentado (ancoragem, escassez/urgência, custo-por-dia, garantia) — não é citar o gatilho, é estruturar a peça inteira nele.
- **Genéricos** — camada por cima de qualquer uma das 4 acima.

## Sugerindo ângulos

1. A partir do nível de funil confirmado no mini-briefing, ler o(s) CSV(s) da(s) categoria(s) correspondente(s) (tabela acima) + sempre considerar Genéricos como opção extra.
2. Cruzar com o contexto do projeto (persona, dores/desejos, diferenciais reais) pra pré-selecionar **4 a 6 ângulos candidatos** — não despejar os 15-20 da categoria inteira.
3. Apresentar cada candidato de forma curta: nome do ângulo + 1 linha de explicação de por que ele encaixa nesse projeto especificamente (não só colar a explicação genérica da planilha).
4. Se o usuário quiser ver mais opções, outra categoria, ou o prompt/exemplo completo de algum ângulo específico, mostrar sob demanda.
5. Esperar o usuário escolher **um ângulo** antes de escrever qualquer copy.

## Escrevendo a copy

Depois do ângulo escolhido, montar a peça na vertente pedida. Em ambas as vertentes valem sempre os 3 elementos de persuasão **obrigatórios** — sem eles a peça não funciona:
- **Benefício** (pelo menos o funcional; dimensional/emocional se couber no espaço).
- **Quebra de objeção** (a mais relevante pro público/produto em questão).
- **Credibilidade** (nem que resumida — uma forma de prova: demonstração, prova social, autoridade, reason why, depoimento etc.).

**Mecanismo** (do problema e/ou da solução) é opcional — só entra se o nível de consciência do público pedir (tipicamente ângulos de categoria Solução).

**Gatilhos mentais** (novidade, urgência, escassez, exclusividade, curiosidade) reforçam mas precisam ser reais — nunca forçar urgência/escassez falsa.

### Vertente "criativo estático"

- **Headline** = 1 hook só (o ângulo escolhido é o eixo central dela). Nunca empilhar dor + prova + oferta na mesma linha.
- **Copy** = 1-2 frases curtas — resolução/prova/quebra de objeção, o que não coube na headline.
- **CTA** = comando seco, nunca vago ("Fale com a gente →", "Envie seu projeto.") — proibido "saiba mais" sem contexto.
- **Direção de arte** — composição, o que a imagem precisa mostrar, o que evitar (ver seção própria abaixo).

### Vertente "roteiro de vídeo"

Estrutura em 3 partes — a "estrutura invisível" é a escolha de quais elementos de persuasão entram em cada uma (referência completa em `Gerador de anúncios/ESTRUTURA "INVISÍVEL" DOS ANÚNCIOS.md`):

- **Gancho** (primeiros segundos) — função é **segmentar**, não vender ainda: quem vê, o que é dito/mostrado/escrito precisa deixar claro pra quem é aquilo. Pode abrir com qualquer elemento (curiosidade, credibilidade, promessa direta/indireta, mecanismo, quebra de objeção) — o ângulo escolhido geralmente dita qual.
- **Corpo** — a maior parte do roteiro: benefício (funcional→dimensional→emocional), quebra de objeção, credibilidade, mecanismo (se aplicável), gatilhos mentais.
- **CTA** — pedir a ação, dizer o que acontece depois do clique ("preenche o formulário", "assiste o vídeo"), e pode reforçar com benefício/urgência/escassez real no próprio CTA.

Escrever o roteiro marcando os blocos (Gancho / Corpo / CTA) explicitamente, não como texto corrido — quem recebe precisa conseguir gravar direto em cima disso.

## Sub-ferramenta opcional — Método FORJA (mecanismo proprietário)

**Só acionar se o usuário pedir explicitamente** (ex.: "cria um mecanismo pra esse produto", "quero um mecanismo próprio", "os ângulos de Solução genéricos não bastam") — nunca automaticamente, mesmo quando o ângulo escolhido é de categoria Solução.

Quando pedido: seguir as 5 fases do Método FORJA (F-O-R-J-A) descritas em `Gerador de anúncios/MÉTODO FORJA para  pesquisa e criação de mecanismos.md`, usando os 10 tipos de mecanismo de `Gerador de anúncios/Biblioteca de Mecanismos de Copy para Anúncios - @renanmsap.md` na Fase J. Regras próprias dessa sub-ferramenta (não confundir com as regras de copy enxuta abaixo): nunca inventar vilão/prova/dado sem pesquisar, sinalizar o que veio de pesquisa própria vs. briefing, aplicar régua ética extra em nicho regulado (saúde, financeiro). O mecanismo resultante (UMS) vira o ângulo/mecanismo usado no roteiro ou peça seguinte.

## Regras de COPY — ENXUTA E OBJETIVA (guardrail padrão Colli&Co, sempre, mesmo com skill do cliente)

- **Headline/gancho = 1 hook só.** Nunca empilhar dor + prova + oferta na mesma linha.
- **Copy = 1–2 frases curtas** (estático); **corpo direto ao ponto** (roteiro) — cada bloco tem 1 função.
- **CTA = comando seco, nunca vago** — proibido "saiba mais" sem contexto.
- Na dúvida, a versão mais curta. Cortar orações subordinadas, qualificadores e repetição.

Isso é o piso — a skill/contexto do cliente pode adicionar tom (ex.: mais provocativo, mais caloroso) por cima, nunca soltar a mão dessa regra de tamanho/objetividade.

## Direção de arte — o que sempre confirmar antes de fechar a peça

- **Paleta/identidade visual oficial** — checar kit de marca (Drive) antes de fixar cor final; se a fonte tiver conflito entre documentos, tratar como hipótese e sinalizar, não travar o rascunho por isso — só a aprovação final de cor.
- **Fotografia/imagem** — priorizar acervo real do cliente sobre banco de imagem genérico ou IA, principalmente quando "vivência real"/autenticidade for pilar de marca.
- **Formatos de entrega** — confirmar tamanho e quantidade por peça antes de produzir em escala; não presumir sem checar o briefing/pedido.
- **Elementos exclusivos de marca** (ícone, logo, selo de prova social) — nunca usar o de uma marca irmã/linha de produto diferente na peça errada.

## Saída — formato por peça

Formato fixo, sempre — cabeçalho com os metadados em negrito, separador, depois o texto da peça em blocos com `###`:

```
---

**Vertente:** criativo estático / roteiro de vídeo
**Ângulo usado:** <nome do ângulo> (categoria <Problema/Solução/Produto/Oferta/Genéricos>)
**Nível de funil:** topo / meio / fundo
**Marca:** <marca ou sub-marca específica da peça, se houver mais de uma no projeto>

---

### GANCHO
<texto>

### CORPO
<texto>

### CTA
<texto>
```

Pra vertente estático, os blocos viram `### HEADLINE`, `### COPY`, `### CTA`, `### DIREÇÃO DE ARTE` (mesma estrutura de cabeçalho + separador antes).

Regras desse formato:
- O cabeçalho de metadados (Vertente/Ângulo usado/Nível de funil/Marca) vem sempre antes do texto, nunca misturado com ele.
- Cada bloco do texto (Gancho/Corpo/CTA ou Headline/Copy/CTA/Direção de arte) é um `###` separado — nunca texto corrido sem divisão, mesmo quando a peça é curta.
- Se houver mais de uma persona/marca envolvida no projeto (ex.: duas sub-marcas), o campo **Marca** deixa explícito pra qual das duas é aquela peça específica.
- Esse é o formato de entrega padrão desta skill — usar sempre, nas duas vertentes, sem precisar o usuário pedir de novo a cada peça.

Quando várias peças compartilham o mesmo conceito visual, não repetir a direção de arte peça a peça — escrever um bloco "Conceito visual geral" uma vez só, e por peça só a variação específica.

## Padrão de iteração — refinar headline/gancho/copy em rodadas curtas

- Quando o usuário rejeitar ou pedir pra "melhorar" um campo específico, **não regravar o documento inteiro** — oferecer 2-3 variações novas só daquele campo, em texto simples (não usar ferramenta de pergunta estruturada pra isso — prefira listar as opções direto na resposta).
- Aplicar o feedback **em todas as peças onde o mesmo padrão se repete**, não só na que foi citada.
- Quando o usuário aprovar uma peça ("ficou ótima", "aprovada"), marcar como travada e não reescrever ela de novo em rodadas seguintes.
- Se o usuário pedir um ajuste de formatação global (ex.: "tira travessão", "tira emoji"), varrer o **documento inteiro**.
- No fim de cada rodada de ajuste, sempre entregar o **documento consolidado inteiro atualizado**.

## Sinais de copy fraca — evitar mesmo quando "está correto"

- **"Não precisa..." como abertura de headline/gancho** — soa defensivo/genérico. Preferir afirmação direta do benefício.
- **Valor/preço citado de forma literal e crua na headline** — statement de venda, não gancho. Se o preço for parte do argumento, cabe melhor no corpo, não na headline.
- **Verbo "resolve/resolveu" como muleta** — variar com verbos mais concretos (cuida, monta, organiza, acompanha).
- **Forçar "confiança/credibilidade" como eixo de venda sem autoridade construída** — se é marca nova/linha de expansão sem histórico próprio, vender pelo diferencial concreto (economia de tempo, preço, conveniência), não por "confie na gente".
- **Jargão interno/B2B na copy do consumidor final** — usar o vocabulário que o próprio cliente usaria pra descrever a própria compra.
- **Contraponto/comparação que não corresponde a nada real** — todo contraste precisa ter um "de quê" real por trás.
- **Prometer característica que não vale pra todo o escopo da peça** — checar se o benefício citado é válido pra todo o universo que a peça endereça, não só pro caso mais forte.
- **Urgência/escassez forçada** — só usar se for real; público percebe quando é falso.

## O que NUNCA fazer

- Escrever a copy antes de sugerir ângulos e o usuário escolher um.
- Aplicar tom/regra de um cliente pra outro por analogia sem checar o contexto real dele.
- Headline/gancho com mais de 1 ideia, copy/corpo longo e empilhado, CTA vago.
- Citar concorrente nominalmente ou fazer promessa que o cliente proibiu, sem checar as regras específicas dele primeiro.
- Fechar paleta/formato final sem confirmar contra o kit de marca oficial quando ele existir.
- Ignorar que já existe uma skill `criar-copy-<cliente>` mais específica — ela sempre tem prioridade de tom/regras sobre esta.
- Reescrever peça já aprovada pelo usuário numa rodada de ajuste seguinte sem necessidade.
- Aplicar pedido de ajuste de formatação só no trecho citado, deixando o resto do documento inconsistente.
- Rodar o Método FORJA sem o usuário ter pedido explicitamente.
- Omitir benefício, quebra de objeção ou credibilidade da peça final — são obrigatórios em qualquer vertente.
