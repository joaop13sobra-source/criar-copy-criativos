# Staging — reforma da skill criar-copy-criativos (2026-09-19)

**STATUS: concluído.** O SKILL.md já foi reescrito com este material —
ver `skills-gerais/criar-copy-criativos/SKILL.md`. Este arquivo fica só
como registro histórico dos insumos e das decisões tomadas (ver
respostas às perguntas em aberto, no fim deste arquivo). Decisões
finais: (1) biblioteca de formatos virais — não incorporada, não
necessária; (2) escopo — fluxo de 1 peça por vez, não modo lote; (3)
Método FORJA — sub-ferramenta só sob pedido explícito do usuário.

Notas acumuladas enquanto o usuário passa os materiais, antes de reescrever
o SKILL.md de uma vez. Não é a skill final — é rascunho de insumos.

## Objetivo da reforma (pedido do usuário)

A skill passa a ter **duas vertentes**: "copy para criativo estático" e
"copy para roteiro de vídeo". Fluxo novo, nessa ordem:

1. Perguntar qual vertente: **criativo estático** ou **roteiro de vídeo**.
2. Independente da vertente, acessar a Biblioteca de Ângulos de Copy
   (Google Sheets, ver abaixo) para embasar a copy.
3. Perguntar **para qual projeto** é a copy.
4. Acessar a pasta do projeto respondido pra puxar contexto (igual ao
   Passo 0 já existente na skill: skill própria > contexto > DCC/UCM >
   CLAUDE.md).
5. Com o contexto do projeto + a biblioteca de ângulos, **sugerir ângulos**
   (da planilha) pro usuário escolher.
6. Usuário escolhe o ângulo.
7. Criar a copy a partir do ângulo escolhido, na vertente correspondente
   (estático ou roteiro).

Ainda faltam 2 materiais do usuário antes de reescrever o SKILL.md:
1. Como criar roteiros (estrutura).
2. Como criar "anúncios infinitos" (estrutura/lógica de combinação).

## Fonte: Biblioteca de Ângulos de Copy para Anúncios (Google Sheets)

- Planilha: "Biblioteca de Ângulos de Copy para Anúncios - João Pedro"
- URL: https://docs.google.com/spreadsheets/d/1xFyUHznjlzZbijIYaTaQAOrlRTp21w-XKFrrxquwo3w/edit
- Acesso: já legível via Service Account
  (`antigravity@n8n2-472719.iam.gserviceaccount.com`, ver
  `skills-gerais/google-sheets-write-access.md`)
- Abas e contagem de ângulos (aba Índice):
  - Índice
  - Problema — 20 ângulos (dor, medo, inimigo, crenças e erros)
  - Solução — 18 ângulos (mecanismo, novidade, transformação, método)
  - Produto — 15 ângulos (prova, autoridade, diferenciais, identidade)
  - Oferta — 16 ângulos (preço, escassez, garantia, condições)
  - Genéricos — 9 ângulos (formato e atenção, funcionam sobre qualquer
    categoria)
  - Total: 78 ângulos
- Estrutura de cada aba de categoria: 5 colunas — `# | Ângulo | Explicação
  | Exemplo | Prompt`.
- Exemplos foram escritos pros nichos de serviços financeiros e
  infoprodutos — adaptar ao nicho real do cliente/projeto.
- Prompts têm campos entre colchetes pra substituir: `[avatar]`,
  `[problema]`, `[solução]`, `[produto]`, `[oferta]` etc. — geram
  **ideias**, não o anúncio pronto; sempre precisam de refino/reescrita
  depois (aplicar o guardrail de copy enxuta já existente na skill).
- **Ainda não lido célula a célula**: só a aba Índice foi lida até agora.
  Antes de finalizar a skill, ler as 5 abas de categoria completas (todas
  as linhas, todas as colunas) pra ter o conteúdo real dos 78 ângulos
  disponível (ou pelo menos o método de puxar sob demanda por categoria).

## Fonte: transcrição da aula sobre a planilha

Arquivo original: `transcricao-2026-09-19.md` (raiz de `Projetos V4`,
gravação 2026-09-19 15-38-33.mov). Conteúdo já absorvido, resumo:

- **Problema que a planilha resolve**: anunciantes rodam anúncios sempre
  pro mesmo público/nível de consciência dentro do público total —
  anúncio "cansa" rápido mesmo com segmentação de público aberto, porque
  atinge sempre o mesmo recorte de pessoas.
- **Ângulo = o ponto de vista central do anúncio.**
  - Ângulo **≠ gatilho mental** (ainda que pareça, principalmente na
    categoria Oferta).
  - Ângulo **≠ formato**. Formato (caixinha de pergunta, entrevista na
    rua, etc.) é reaproveitável em qualquer ângulo — a combinação
    formato × ângulo é o que gera "anúncios infinitos" (ainda vou receber
    o direcionamento formal de como estruturar isso).
- **Lógica das 5 categorias por nível de consciência**:
  - **Problema** — fala só da dor, sem mencionar a solução ainda. Mira
    quem está inconsciente ou recém consciente do problema ("acordar" a
    pessoa pro problema).
  - **Solução** — já pressupõe consciência do problema; foca em
    mecanismo único, novidade, comparação de métodos, atalho,
    simplicidade — sem ainda vender o produto especificamente.
  - **Produto** — prova social, ser específico, estudo de caso, resultado
    de aluno/cliente, depoimento de terceiros.
  - **Oferta** — o anúncio inteiro gira em torno de UM eixo tipo gatilho
    mental sustentado do início ao fim (ancoragem, escassez/urgência,
    custo-por-dia, garantia) — não é "citar" o gatilho, é estruturar a
    peça inteira nele.
  - **Genéricos** — funcionam sobre qualquer uma das 4 categorias acima:
    curiosidade (geralmente via número: "3 motivos pelos quais..."),
    polêmica/opinião impopular (gera engajamento → CPM mais barato),
    desafio/teste, psicologia reversa, analogia (simplifica conceito
    abstrato).
- Cada ângulo tem explicação + exemplo genérico + (às vezes) exemplo real
  com link + prompt de geração de ideia (trocar `[avatar]` etc.).
- Recomendação do autor: testar muitos formatos × muitos ângulos
  diferentes.

## Fonte: "ESTRUTURA 'INVISÍVEL' DOS ANÚNCIOS" (estrutura de roteiro)

Arquivo original: `~/Downloads/ESTRUTURA "INVISÍVEL" DOS ANÚNCIOS.md`
(baixado 2026-09-19). Ainda falta o usuário passar o "como usar" desse
material — isto abaixo é só a estrutura em si.

- **Ideia central**: todo anúncio/roteiro tem uma estrutura invisível =
  a ordem em que os elementos de persuasão aparecem dentro do roteiro.
  Isso é uma camada **ortogonal ao ângulo** da Biblioteca de Ângulos —
  o ângulo é o ponto de vista central (problema/solução/produto/oferta/
  genérico); a estrutura invisível é como esse ângulo é *organizado* em
  gancho → corpo → CTA usando os 8 elementos de persuasão abaixo.

- **8 elementos de persuasão** (blocos que se combinam):
  1. Benefício funcional
  2. Benefício dimensional
  3. Benefício emocional
  4. Quebra de objeção (tempo, dinheiro, esforço, conhecimento, risco)
  5. Credibilidade (demonstração, motivo lógico/reason why, autoridade,
     estudos científicos, depoimentos, resultados, prova social,
     humildade, reconhecer ceticismo, reduzir a promessa)
  6. Mecanismo do problema (a causa do problema)
  7. Mecanismo da solução (o que combate essa causa)
  8. Gatilhos mentais (novidade, urgência, escassez, exclusividade,
     curiosidade)

- **Roteiro em 3 partes**: Gancho → Corpo → Chamada para ação (CTA).
  A estrutura invisível é a combinação desses 8 elementos dentro de
  cada uma das 3 partes — e existem infinitas combinações possíveis
  (o arquivo lista 14 exemplos de "receitas" de estrutura, ex.: "Gancho
  com credibilidade + quebra de objeção; Benefício funcional + benefício
  dimensional; Mecanismo; CTA pro formulário com escassez/urgência").

- Exemplos de gancho do arquivo:
  - Curiosidade + benefício funcional direto: "Como que você, médico,
    pode ganhar R$5 mil num dia sem precisar pisar no hospital?"
  - Credibilidade + benefício dimensional indireto: "Acabei de ver uma
    matéria na Globo de um médico que conseguiu parar de depender de
    plantões aos 35 anos"

- **Como isso deve se encaixar na skill (hipótese, confirmar com o
  usuário quando reescrever)**: pra vertente "roteiro de vídeo", depois
  de escolher o ângulo (da Biblioteca de Ângulos), usar essa estrutura
  invisível pra organizar o roteiro em Gancho/Corpo/CTA, escolhendo
  quais dos 8 elementos de persuasão entram em cada parte (uma das 14
  receitas do arquivo, ou combinação livre). Ainda falta o "como usar"
  que o usuário vai mandar — pode mudar esse encaixe.

## Fonte: transcrição parte 2 — elementos de persuasão + como usar a estrutura invisível

Arquivo original: `transcricao-2026-09-19-parte2.md` (raiz de
`Projetos V4`, gravação 2026-09-19 15-53-02.mov). Esse é o "como usar" do
arquivo "Estrutura Invisível dos Anúncios" — explica cada um dos 8
elementos de persuasão e como eles entram no roteiro.

- **Premissa**: variar só o ângulo não basta — o anúncio precisa ser
  "forte" nos elementos de persuasão, senão não convence ninguém a agir
  (clicar, comprar, se cadastrar, mandar mensagem, seguir).

- **Benefício** (3 camadas, ideal citar as três em sequência, não só a
  óbvia):
  1. **Funcional** — o benefício óbvio/direto (ex.: ganhar R$500/mês,
     emagrecer 3kg).
  2. **Dimensional** — a consequência prática na vida real daquele
     benefício funcional (ex.: poder viajar, voltar a usar a roupa que
     gostava).
  3. **Emocional** — a consequência emocional (ex.: ficar tranquilo,
     não sentir mais vergonha do corpo).
  - Sem benefício, "ninguém tá nem aí" pro anúncio.

- **Quebra de objeção** — as 5 objeções universais: tempo, dinheiro,
  esforço, conhecimento, risco. Pode quebrar de forma direta ("15 min por
  dia", "mais barato que uma pizza", "iniciante consegue", "100%
  natural", "mais seguro que renda fixa"). **Exceção deliberada**: se o
  produto realmente exige algo (ex.: é caro de verdade), pode usar isso
  como **filtro** pra afastar quem não é o público certo, em vez de
  tentar esconder.

- **Credibilidade** — obrigatória porque a maioria do público nunca viu
  o anunciante antes. Formas de provar (usar uma ou combinar):
  demonstração (a mais forte — mostrar, não só dizer), prova de resultado
  de terceiros/prova social, motivo lógico (reason why: dar o motivo de
  uma oferta aumenta a credibilidade dela), autoridade (prêmios, mídia,
  selo, citar autoridade de terceiros), estudos científicos, depoimento
  de alunos/resultado próprio, prova social por volume ("10 mil alunos"),
  humildade, reconhecer o ceticismo do público ("sei que parece bom
  demais pra ser verdade"), reduzir a promessa pra ficar mais crível
  (achar o meio-termo entre forte demais/fraca demais).

- **Mecanismos** (opcionais, dependem do nível de consciência do
  público):
  - **Mecanismo do problema** — a causa real do problema (ex.:
    "você não emagrece porque seu metabolismo está lento"). Pode incluir
    eliminar soluções erradas alternativas.
  - **Mecanismo da solução** — o que combate essa causa especificamente.
  - Produto e solução **não são a mesma coisa** (mecanismo é da solução
    em si, produto é o veículo que entrega essa solução).

- **Gatilhos mentais**: novidade e exclusividade (ajudam a capturar
  atenção no gancho), curiosidade (ajuda a reter até o final — se a
  pessoa pula antes, não vê o CTA), urgência (motivo real pra agir
  agora), escassez (vagas/estoque/agenda limitados). **Urgência e
  escassez precisam ser reais** — público percebe quando é forçado.

- **O que é obrigatório vs. opcional**: **benefício + quebra de objeção +
  credibilidade são sempre obrigatórios** (sem eles o anúncio não
  funciona). **Mecanismo é opcional**, depende do nível de consciência do
  público (equivalente à lógica de categorias da Biblioteca de Ângulos:
  público já ciente da solução não precisa do mecanismo do problema
  reexplicado, por exemplo).

- **Roteiro (gancho/corpo/CTA) detalhado**:
  - **Gancho** — função é **segmentar**, não vender ainda: quem vê, o que
    é dito/mostrado/escrito na tela nos primeiros segundos precisa deixar
    claro pra quem é aquilo (ex.: "exclusivo pra médicos com +300 mil de
    patrimônio" + imagem de médico). O formato (caixinha de pergunta
    etc.) ajuda a construir esse gancho, mas gancho é sobre
    segmentação, não formato.
  - **Corpo** — a maior parte do anúncio; é onde entram benefício, quebra
    de objeção, credibilidade, mecanismos, gatilhos mentais.
  - **CTA** — pedir a ação (ex.: "Saiba mais"), dizer o que acontece
    depois do clique ("preenche o formulário", "assiste o vídeo
    gratuito"), e pode reforçar com benefício/urgência/escassez no
    próprio CTA.

- **Confirmação da lógica de combinação ("anúncios infinitos")**: a
  transcrição fecha confirmando exatamente a hipótese que eu tinha
  registrado acima — **estrutura invisível = ordem/escolha de quais
  elementos de persuasão entram em cada parte do roteiro** (tipo montar
  um Lego: pode abrir o gancho com qualquer elemento — credibilidade,
  curiosidade, promessa, mecanismo, quebra de objeção — e encaixar o
  resto depois). **Ângulo (da Biblioteca) × Formato × Estrutura
  invisível** juntos = infinitas combinações de anúncio. Isso responde o
  segundo material pendente ("estrutura de anúncios infinitos") — não é
  um material à parte, é a síntese dos dois arquivos de estrutura
  invisível + a Biblioteca de Ângulos.

## Fonte: "Desafio 100 Anúncios por Dia" (@renanmsap) — ESTE é o material de "anúncios infinitos"

Arquivo: `Desafio 100 Anúncios por Dia - por @renanmsap.md`. Framework de
6 etapas pra escalar produção de anúncios por combinação, não por
criatividade infinita.

- **Ideia central**: escrever poucos anúncios-base (ex.: 5) e multiplicar
  variando ângulo × estrutura × formato gera dezenas/centenas de versões.
  "Criatividade não é escalável, processo sim."
- **As 6 etapas** (as 4 primeiras são criação, a 5ª multiplicação, a 6ª
  otimização — cada etapa alimenta a seguinte):
  1. **Briefing** — levantar TODOS os argumentos antes de escrever:
     credibilidade, promessa, quebras de objeção (+ resposta de cada),
     CTAs, público (dores e desejos). Regra: se sentir falta de um
     argumento na hora de escrever, o briefing tá incompleto — voltar e
     completar.
  2. **Ângulos** — perspectiva por **nível de consciência (Eugene
     Schwartz, 5 níveis)**:
     | Nível | Público | Anúncio precisa |
     |---|---|---|
     | 1. Inconsciente | não sabe que tem o problema | despertar a consciência do problema |
     | 2. Consciente do problema | sente, não conhece soluções | apresentar que existe solução |
     | 3. Consciente da solução | sabe que existem soluções, não a sua | mostrar mecanismo/método |
     | 4. Consciente do produto | conhece o produto, não comprou | provar e quebrar objeções |
     | 5. Totalmente consciente | só falta empurrão | oferta, urgência, CTA direto |
     - Escolher **1-2 ângulos por nível** (da Biblioteca de Ângulos) já
       garante cobertura completa do funil — mapeia quase 1:1 com as
       categorias da planilha: Problema≈níveis 1-2, Solução≈nível 3,
       Produto≈nível 4, Oferta≈nível 5, Genéricos atravessam todos.
     - Pra cada ângulo escolhido, listar os argumentos do Briefing que o
       sustentam.
  3. **Estrutura** — quais elementos de persuasão entram e em que ordem
     (é a "estrutura invisível" dos outros 2 arquivos). Variáveis pra
     combinar: posição do benefício (começo/meio/fim), tipo de prova
     (social, resultado próprio, lógica, demonstrativa — um tipo
     diferente por anúncio), objeção a quebrar (uma diferente por
     anúncio), dor/desejo a tocar (um diferente por anúncio), gancho
     (visual+textual+falado). Mesmo ângulo + prova diferente = anúncio
     diferente.
  4. **Formatos** — a "embalagem viral": o anúncio precisa parecer
     conteúdo orgânico de Instagram, não propaganda, pra não ser
     ignorado por reflexo. Pegar um anúncio já escrito (ângulo+estrutura
     prontos) e adaptar pra 3-5 formatos de uma "biblioteca de formatos
     virais" — **essa biblioteca de formatos NÃO foi recebida ainda**,
     só é mencionada/referenciada no material (ver pendência abaixo).
  5. **Multiplicação** — a matemática: **ÂNGULO × ESTRUTURA × FORMATO =
     ANÚNCIO ÚNICO**. Ex.: 1 ângulo em 3 estruturas = 3 anúncios; cada um
     em 5 formatos = 15 anúncios; com 7-10 ângulos (1-2 por nível) passa
     de 100 facilmente. Só ~5 anúncios/semana precisam ser
     **escritos** de verdade — o resto é montagem/adaptação.
  6. **Métricas** — analisar e otimizar: hook rate/retenção 3s (gancho ou
     formato), tempo médio de visualização (estrutura/comunicação), CTR
     (ângulo/promessa/CTA), CPA (o conjunto). Ciclo: rodar lote → esperar
     volume (≥100 cliques/anúncio) → isolar vencedores → matar
     perdedores → próximo lote multiplica os vencedores. As métricas do
     lote atual viram o briefing do próximo.
- **Checklist de execução** do autor (útil como checklist final da
  skill): briefing completo → 1-2 ângulos por nível → argumentos
  mapeados por ângulo → estrutura definida por anúncio (benefício+prova+
  objeção+dor/desejo) → 4-5 anúncios-base escritos → cada um adaptado
  pra 3-5 formatos → nomenclatura organizada (ângulo/estrutura/formato)
  pra rastrear métrica depois → métricas analisadas → próximo lote a
  partir dos vencedores.
- Rodapé do arquivo é pitch comercial do autor (serviço/consultoria) —
  **não é material a incorporar na skill**, ignorar.

## Fonte: "MÉTODO FORJA" — pesquisa e criação de mecanismos (@renanmsap)

Arquivo: `MÉTODO FORJA para  pesquisa e criação de mecanismos.md`.
Processo profundo (5 fases: F-O-R-J-A) pra **pesquisar e nomear um
mecanismo único (UMS/UMP)** quando o ângulo escolhido é de categoria
**Solução** (mecanismo/novidade/método) e o mercado já está saturado de
mecanismos genéricos — não é pra rodar em toda copy, é uma ferramenta de
pesquisa mais pesada, pensada originalmente pra ser executada como
prompt separado (anexando um briefing de copy + o próprio metodoforja.md
numa conversa dedicada).

- **F — Fotografe o mercado**: diagnóstico de 1 página. Coletar 20-30
  anúncios/VSLs do nicho, classificar estágio de sofisticação (1-2 só
  promessa crua / 3-4 promessa+mecanismo nomeado / 5 identidade), listar
  mecanismos já queimados (não colidir) e a promessa morta mais desejada
  a ressuscitar.
- **O — Obtenha a matéria-prima**: dossiê com ≥5 candidatos a vilão e ≥5
  a caminho, pesquisados em 4 territórios (o problema em si, o prospect
  via reviews/Reddit, entrevista com o criador do produto, ponto de
  falha de cada solução rival).
- **R — Reenquadre o problema (UMP = vilão)**: o vilão em ≤2 frases,
  passando 4 filtros (explica fracassos passados? isenta o prospect de
  culpa? é verificável? não colide com lista negra?). Template: "A
  verdadeira razão de [problema] não é [causa aceita] — é [vilão]."
- **J — Junte caminho, nome e história (UMS = mecanismo)**: nome do
  mecanismo (como fenômeno, não como produto) + cadeia causal em 2
  frases + genesis story + prova em 2 camadas (analogia intuitiva +
  evidência empírica). Usa os **10 tipos de mecanismo** da Biblioteca de
  Mecanismos (ver próxima seção) pra gerar 3 opções de caminho antes de
  escolher.
- **A — Afie e aplique**: validar nos 8 testes (meme, "nunca pensei
  assim", absolvição, histórico, exclusividade, dupla prova, entrega,
  sofisticação) + mapa de implantação em headline/lead/corpo/oferta/
  anúncios.
- Regra ética: nunca inventar vilão/prova/dado; sinalizar quando algo
  vem de pesquisa própria vs. briefing; nicho regulado (saúde,
  financeiro) exige régua ética extra — nenhuma alegação sem sustentação.
- **Relação com a skill (hipótese)**: isso é uma sub-ferramenta opcional
  pra quando o ângulo é de categoria Solução E o usuário quer um
  mecanismo proprietário de verdade (não só usar um ângulo pronto da
  planilha) — acionar só sob pedido explícito, não em toda copy.

## Fonte: "Biblioteca de Mecanismos de Copy para Anúncios" (@renanmsap)

Arquivo: `Biblioteca de Mecanismos de Copy para Anúncios - @renanmsap.md`.
Os **10 tipos de mecanismo** (as "alavancas" psicológicas usadas na Fase
J do Método FORJA pra nomear o UMS) — cada um com a razão psicológica por
trás + 3 exemplos reais:

1. **Ingrediente/Componente** — isola 1 elemento tangível (ex.:
   piritionato de zinco no Head & Shoulders). Risco: se o ingrediente é
   genérico, exclusividade dura pouco — combinar com Fonte/Origem ou
   Dose/Proporção.
2. **Processo/Método** — a sequência/ordem, não os insumos (ex.: P90X
   "Muscle Confusion", Técnica Pomodoro). Forte quando os componentes já
   são commodity.
3. **Timing/Janela** — desloca "o quê" pra "quando" (ex.: janela
   anabólica pós-treino, jejum intermitente). Gera urgência sem precisar
   fabricar.
4. **Dose/Proporção** — não muda o comportamento, ajusta uma métrica
   (ex.: proporção ômega-6/ômega-3, regra 80/20). Valida escolhas
   passadas em vez de invalidar.
5. **Eliminação** — pedir pra parar é mais leve que pedir pra começar
   (ex.: dietas de eliminação, método KonMari). Reenquadra como excesso
   tóxico, não carência.
6. **Combinação/Sinergia** — nenhum elemento isolado é exclusivo, mas a
   combinação é (ex.: sistema Proactiv de 3 passos, stack whey+creatina).
7. **Fonte/Origem** — a procedência garante qualidade (ex.: Schlitz e a
   água de poço artesiano, café single origin, "made in Germany").
8. **Tecnologia/Ferramenta** — atribui o resultado ao instrumento, não à
   habilidade (ex.: modo retrato por IA, robôs de trading). Democratiza
   a promessa pra quem já fracassou tentando adquirir a habilidade.
9. **Informação/Fórmula** — um dado/cálculo que o mercado ignora (ex.:
   Índice de Sharpe, calculadora de TMB personalizada). Mais barato
   psicologicamente: não exige mudar comportamento, só saber algo novo.
10. **Pessoa/Dom** — atribui o resultado a quem executa, não ao método
    (ex.: ex-auditor vendendo consultoria tributária, preparador de
    atletas olímpicos). Mais forte pra justificar preço premium, menos
    escalável.

- Um mecanismo forte costuma **combinar 2 alavancas** (ex.: Ingrediente +
  Fonte, como a Schlitz; Processo + Timing, como protocolos cronometrados).
- Teste de sanidade: remover o elemento central — a promessa ainda se
  sustenta? Se sim, não é mecanismo de verdade, é enfeite em cima de
  promessa genérica.

## Onde estão todos os arquivos-fonte agora

Pasta: `skills-gerais/criar-copy-criativos/Gerador de anúncios/`
- `transcricao-2026-09-19.md` — aula sobre a Biblioteca de Ângulos.
- `transcricao-2026-09-19-parte2.md` — elementos de persuasão + como usar
  a estrutura invisível.
- `ESTRUTURA "INVISÍVEL" DOS ANÚNCIOS.md` — os 8 elementos + roteiro em 3
  partes + 14 receitas de combinação.
- `Desafio 100 Anúncios por Dia - por @renanmsap.md` — as 6 etapas de
  multiplicação (Briefing→Ângulos→Estrutura→Formatos→Multiplicação→
  Métricas) = o material de "anúncios infinitos".
- `MÉTODO FORJA para  pesquisa e criação de mecanismos.md` — as 5 fases
  (F-O-R-J-A) pra criar um mecanismo proprietário (UMS/UMP).
- `Biblioteca de Mecanismos de Copy para Anúncios - @renanmsap.md` — os
  10 tipos/alavancas de mecanismo usados na Fase J do Método FORJA.
- `biblioteca-angulos_Índice.csv`, `biblioteca-angulos_Problema.csv`,
  `biblioteca-angulos_Solução.csv`, `biblioteca-angulos_Produto.csv`,
  `biblioteca-angulos_Oferta.csv`, `biblioteca-angulos_Genéricos.csv` —
  export completo (todas as linhas/colunas) das 6 abas da planilha de
  ângulos, puxado via Service Account em 2026-09-19.

## Pontos em aberto pra confirmar com o usuário antes de reescrever o SKILL.md

- [ ] **Biblioteca de formatos virais** é citada pelo "Desafio 100
      Anúncios" (etapa 4) mas **nunca foi recebida** — a skill vai
      precisar dela pra vertente estático/roteiro, ou fica só como
      referência conceitual (sem lista concreta de formatos) até o
      usuário mandar?
- [ ] **Escopo da skill**: o pedido original do usuário era um fluxo
      *interativo de 1 peça por vez* (vertente → projeto → sugerir
      ângulos → usuário escolhe 1 → criar 1 copy). O "Desafio 100
      Anúncios" é um framework de *produção em lote* (5 anúncios-base ×
      estrutura × formato = 100+). A skill deve **só usar o framework de
      lote como pano de fundo conceitual** (ângulos por nível de
      consciência, estrutura de persuasão) mas manter a interação
      original de 1 peça por vez? Ou a skill deve **também** oferecer um
      modo de gerar um lote/múltiplas variações de uma vez (multiplicando
      ângulo×estrutura×formato) quando o usuário pedir?
- [ ] **Método FORJA / Biblioteca de Mecanismos**: entram na skill como
      sub-ferramenta opcional (só quando o usuário pedir explicitamente
      "cria um mecanismo" ou o ângulo escolhido for de categoria
      Solução/mecanismo), ou ficam de fora do fluxo principal e só como
      referência na pasta "Gerador de anúncios" pra uso manual?
- [ ] Decidir formato final: SKILL.md referencia os CSVs/MDs da pasta
      "Gerador de anúncios" (ler sob demanda) em vez de embutir tudo no
      corpo do arquivo (evitar um SKILL.md gigante).
- [ ] Reescrever `SKILL.md` com as duas vertentes (estático / roteiro),
      o fluxo de escolha de ângulo, e a integração da estrutura de
      persuasão + (se aplicável) multiplicação/mecanismo.
