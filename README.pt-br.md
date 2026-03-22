<div align="center">

# Dialex

### Amplificador Cognitivo de Busca

**Debate multi-mente que produz conhecimento emergente**

*"dia" (atraves/entre, Grego) + "lex" (palavra/lei, Latim) — conhecimento atraves do dialogo*

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Status: MVP](https://img.shields.io/badge/status-MVP%20em%20desenvolvimento-orange.svg)]()

[English](README.md) | **Portugues** | [Espanol](README.es.md) | [中文](README.zh-cn.md)

</div>

---

## O que e o Dialex?

Imagine uma mesa redonda onde os autores dos livros que voce mais respeita discutem entre si — e dessa discussao nasce um livro novo que nenhum deles escreveria sozinho.

Isso e o Dialex.

O Dialex e um sistema onde **multiplas mentes AI especialistas** — cada uma com um metodo de raciocinio distinto — debatem problemas e produzem conhecimento que **nenhuma mente individual geraria sozinha**. Nao e apenas "perguntar para varios chatbots". E uma orquestracao estruturada onde a divergencia entre perspectivas gera sinteses genuinamente novas.

### Framing honesto

Transparencia e um valor central do projeto. Vamos ser claros sobre o que o Dialex **e** e o que **nao e**:

| Voce pode ouvir | O que realmente acontece |
|-----------------|------------------------|
| "As mentes discordam" | **Divergencia funcional sob restricao** — LLMs nao tem crencas para abandonar. A divergencia vem de prompts e modelos diferentes, nao de compromisso epistemico genuino |
| "Emergencia" | **Novidade combinatoria e estrutural** — o sistema recombina conhecimento existente de formas que uma perspectiva unica nao faria, como um caleidoscopio cognitivo |
| "Clones de mentes" | **Clones de fidelidade de persona** — reproduzem posicoes, estilo e expertise do especialista. Padroes linguisticos, nao arquitetura cognitiva |
| "Debate" | **Divergencia estruturada com sintese** — funcional e produtivo, mas sem as apostas existenciais de um debate humano real |

O Dialex produz resultados valiosos pelo mesmo motivo que ler cinco analistas sobre o mesmo evento e valioso: **amplia o espaco de consideracoes e gera insights candidatos que uma perspectiva unica perderia**.

---

## Funcionalidades Principais

### Knowledge Graph (SQLite + JSON)
- Nos: conceitos, heuristicas, frameworks, valores, contradicoes, sinteses
- Arestas: `supports`, `contradicts`, `derived_from`, `synthesized_from`, `applies_to`
- Busca fulltext via FTS5
- Decaimento temporal — conhecimento nao acessado perde relevancia naturalmente
- Dicionario de pares de contradicao para deteccao automatica de tensoes

### Motor de Debate (3 fases)
- **Fase 1:** Decomposicao multi-perspectiva — duas mentes propoem decomposicoes diferentes do problema, que sao fundidas
- **Fase 2:** Posicoes independentes + mapeamento de tensoes usando o dicionario de contradicoes
- **Fase 3:** Debate estruturado (2-3 rodadas) + sintese + salvamento no grafo
- Modelos diferentes por mente via LiteLLM (anti-sycophancy por arquitetura)
- Recuperacao round-aware: cada rodada busca evidencias NOVAS baseadas no que foi dito na rodada anterior
- Compressao multi-escala em 3 niveis (verbatim/condensado/abstrato) para evitar estouro de contexto

### Perfis de Mente
- Cada mente tem um **metodo de raciocinio estrutural** (nao apenas um rotulo):
  - **Indutivo:** observacoes -> padrao -> generalizacao
  - **Abdutivo:** surpresa -> hipotese -> teste
  - **Analogico:** fonte -> mapeamento -> alvo
- Recuperacao por subgrafo — cada mente ve evidencias DIFERENTES (mecanismo anti-martingale)
- Perfis estaticos em YAML (grafos de identidade dinamica ficam para v2)

### Modo Entrevista
- `*interview {mente} {topico}` — Q&A estruturado sobre o contexto do grafo
- Recupera nos relevantes e sintetiza respostas da perspectiva da mente

### Avaliacao
- Juiz LLM unico (modelo diferente dos debatedores)
- Comparacao com baseline de mente unica — rejeita sintese se nao superar a melhor resposta individual
- Teste da hipotese nula contra um prompt simples multi-perspectiva

### CLI
```bash
dialex debate "Qual a melhor estrategia de precificacao para SaaS B2B?"
dialex interview naval-ravikant "decisoes sob incerteza"
dialex graph "heuristicas sobre risco"
dialex ingest eugene-schwartz
```

---

## Inicio Rapido

### Pre-requisitos
- Python 3.11+
- Uma chave de API de provedor LLM (OpenAI, Anthropic, ou qualquer provedor suportado pelo LiteLLM)

### Instalacao

```bash
# Clone o repositorio
git clone https://github.com/murilloimparavel/dialex.git
cd dialex

# Crie e ative um ambiente virtual
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate   # Windows

# Instale as dependencias
pip install -e ".[dev]"

# Configure sua chave de API
export OPENAI_API_KEY="sua-chave-aqui"
# ou
export ANTHROPIC_API_KEY="sua-chave-aqui"
```

### Primeiro debate

```bash
# Ingira uma mente do MMOS
dialex ingest eugene-schwartz

# Ingira mais mentes para ter diversidade
dialex ingest gary-halbert
dialex ingest naval-ravikant

# Rode seu primeiro debate
dialex debate "Como convencer alguem que nao sabe que tem um problema?"
```

O sistema vai:
1. Selecionar mentes com **maxima diversidade cognitiva** para o problema
2. Decompor a pergunta em sub-questoes de multiplas perspectivas
3. Cada mente elabora sua posicao de forma independente
4. Tensoes e apoios sao mapeados automaticamente
5. Um debate estruturado de 2-3 rodadas acontece
6. Uma sintese emerge — e e salva no knowledge graph
7. O grafo cresce, e o proximo debate se beneficia das sinteses anteriores

---

## Arquitetura

```
PIPELINE MMOS                    COGNITIVE KB GRAPH
(cria as mentes)                 (faz as mentes pensarem juntas)
      |                                |
      v                                v
  *map {pessoa}                  PROBLEMA DO USUARIO
                                       |
                                       v
                          +---------------------+
                          |   SELETOR DE DEBATE  |
                          |  (escolhe mentes com |
                          |   maxima diversidade |
                          |   cognitiva para     |
                          |   este problema)     |
                          +----------+----------+
                                     |
                        +------------+------------+
                        |            |            |
                        v            v            v
                   +---------+  +---------+  +---------+
                   | MENTE A |  | MENTE B |  | MENTE C |
                   | metodo: |  | metodo: |  | metodo: |
                   | indutivo|  | abdutivo|  | analogico|
                   +---------+  +---------+  +---------+
                        |            |            |
                        +-----+------+------+----+
                              |             |
                              v             v
                       +----------+  +----------+
                       | DETECTOR |  | DETECTOR |
                       | DE TENSAO|  | DE APOIO |
                       +-----+----+  +-----+----+
                             |             |
                             v             v
                       +-------------------------+
                       |   MOTOR DE SINTESE      |
                       |  (blending conceitual,  |
                       |   fusao dialetica,      |
                       |   salto abdutivo)       |
                       +------------+------------+
                                    |
                                    v
                       +-------------------------+
                       |  DETECTOR DE EMERGENCIA |
                       |  "Isso e genuinamente   |
                       |   novo ou recombinacao?" |
                       +------------+------------+
                                    |
                                    v
                       +-------------------------+
                       |    KNOWLEDGE GRAPH      |
                       |  (SQLite + JSON)        |
                       |  Nos crescem, decaem,   |
                       |  se reorganizam         |
                       +-------------------------+
```

### Camadas do Sistema

| Camada | Nome | Funcao |
|--------|------|--------|
| 0 | Ingestao MMOS | Converte artefatos de mentes em nos do grafo |
| 1 | Knowledge Graph | Armazenamento, recuperacao e decaimento temporal |
| 2 | Perfis de Mente | Metodos de raciocinio e restricoes cognitivas |
| 3 | Motor de Debate | Selecao, debate estruturado, sintese |
| 4 | Avaliacao | Deteccao de emergencia e controle de qualidade |
| 5 | CLI | Interface de linha de comando |

### Stack Tecnico

| Componente | Tecnologia | Justificativa |
|-----------|-----------|---------------|
| Armazenamento | SQLite + JSON | Local-first, zero infra, confortavel ate ~10k nos |
| Busca fulltext | FTS5 | Nativo do SQLite, ~10 linhas de SQL |
| Multi-provedor LLM | LiteLLM | Modelos diferentes por mente = anti-sycophancy |
| CLI | Python (Click/Typer) | Ergonomia para desenvolvedores |
| Linguagem | Python 3.11+ | Ecossistema LLM mais maduro |

---

## A Ciencia por tras do Dialex

O Dialex foi fundamentado por uma pesquisa com 5 agentes paralelos que analisaram mais de 50 papers academicos em 6 campos. Sete principios emergiram como base cientifica do sistema.

### Principio 1: Diversidade Vence Habilidade

> Hong & Page (PNAS, 2004) — Prova matematica: um time de agentes aleatorios de uma populacao diversa supera um time dos melhores agentes, porque os melhores convergem em abordagem e perdem diversidade. Confirmado por Woolley et al. (Science, 2010) que descobriram um "fator c" mensuravel de inteligencia coletiva que previa 40% da variancia de performance grupal — e NAO era correlacionado com inteligencia media individual.

**No Dialex:** Mentes sao selecionadas para debate por DIVERSIDADE COGNITIVA, nao por qualidade individual.

### Principio 2: Conhecimento Novo Nasce da Colisao de Frames

> Fauconnier & Turner, "Conceptual Blending" (2002); Koestler, "The Act of Creation" (1964) — Blending conceitual: a mente combina elementos de "espacos mentais" diferentes em um "espaco mesclado" onde surge estrutura emergente que nao existe em nenhum input isolado. A "bisociacao" de Koestler: conectar dois quadros de referencia auto-consistentes mas habitualmente incompativeis.

**No Dialex:** O motor de debate forca COLISAO entre frames incompativeis, nao busca concordancia.

### Principio 3: Contradicao e Motor, nao Erro

> Logica Paraconsistente (Newton da Costa, anos 1960+); Engestrom, "Expansive Learning" (2001); Bakhtin, "Dialogismo" (1929/1981) — A logica paraconsistente permite formalmente que afirmacoes contraditorias coexistam sem que o sistema se torne trivial. Engestrom mostra que contradicoes entre sistemas de atividade impulsionam a criacao de conhecimento genuinamente novo.

**No Dialex:** Arestas `contradicts` no grafo sao as MAIS VALIOSAS. O sistema ativamente busca e preserva contradicoes.

### Principio 4: Especialistas Pensam por Padroes, nao Regras

> Klein, "Recognition-Primed Decision" (1998); Dreyfus, "Five-Stage Model" (1980); Leonard, "Deep Smarts" (2005) — Especialistas nao analisam opcoes — reconhecem padroes e simulam mentalmente um unico curso de acao. No nivel expert, regras sao internalizadas ate a invisibilidade.

**No Dialex:** Cada mente tem HEURISTICAS (quando X, faca Y, porque Z) extraidas da pratica, nao regras abstratas.

### Principio 5: Conhecimento Nasce nas Fronteiras entre Comunidades

> Wenger, "Communities of Practice" (1998); Star & Griesemer, "Boundary Objects" (1989); Galison, "Trading Zones" (1997) — Inovacao nao acontece no centro da expertise — acontece na FRONTEIRA entre dominios. Objetos de fronteira permitem troca sem exigir consenso.

**No Dialex:** Nos de sintese gerados por debates sao OBJETOS DE FRONTEIRA — pertencem a multiplas mentes sem ser exclusivos de nenhuma.

### Principio 6: O Grafo se Auto-Organiza em Estado Critico

> Buehler (MIT), "Agentic Deep Graph Reasoning Yields Self-Organizing Knowledge Networks" (2025, Nature/Springer) — Knowledge graphs que crescem por inferencia alcancam um ESTADO CRITICO (borda do caos) onde descoberta continua e possivel. Os grafos resultantes sao redes scale-free com nos-hub e nos-ponte emergentes.

**No Dialex:** O grafo nao precisa de um esquema rigido. Ele cresce organicamente com cada debate e auto-organiza clusters.

### Principio 7: Persona nao Basta — Metodos de Raciocinio Distintos sao Obrigatorios

> DMAD, "Breaking Mental Set to Improve Reasoning through Diverse Multi-Agent Debate" (ICLR, 2025); ChatEval (ICLR, 2024) — Atribuir personas diferentes a LLMs nao funciona — eles colapsam para o mesmo raciocinio. O que funciona e forcar metodos de raciocinio GENUINAMENTE DIFERENTES.

**No Dialex:** Cada mente nao e apenas "persona + base de conhecimento". Ela tem um METODO DE RACIOCINIO DISTINTO (indutivo, abdutivo, analogico, heuristico, dialetico, etc.).

---

## Construido Sobre

### MMOS — Mind Mapping & Orchestration System

O Dialex opera sobre mentes criadas pelo **MMOS** (Mind Mapper OS v4.0 "Legendary Agents"), criado por **Alan Nicolas**.

O MMOS e o pipeline upstream que cria clones de mentes especialistas usando a **metodologia DNA Mental de 8 camadas**:

| Camada | Nome | O que captura |
|--------|------|---------------|
| L1 | Padroes Comportamentais | Acoes observaveis, decisoes, comportamentos recorrentes |
| L2 | Estilo de Comunicacao | Padroes linguisticos, vocabulario, tom, DNA de voz |
| L3 | Rotinas e Habitos | Padroes temporais, rituais diarios, habitos de trabalho |
| L4 | Padroes de Reconhecimento | Radares mentais — o que a pessoa nota e o que ignora |
| L5 | Modelos Mentais | Frameworks de pensamento, interpretacao da realidade |
| L6 | Hierarquia de Valores | Valores centrais ranqueados por evidencia de sacrificio |
| L7 | Obsessoes Centrais | Forcas motrizes, loops de pensamento, interesses fundidos a identidade |
| L8 | Paradoxos Produtivos | Contradicoes que fazem o clone parecer humano |

> A **Camada 8 e a camada de ouro.** Paradoxos sao o que separa um clone robotico de um que parece autenticamente humano. No Dialex, esses paradoxos se tornam arestas `contradicts` — as arestas mais valiosas do grafo.

O Dialex pega onde o MMOS para: o MMOS cria mentes individuais com alta fidelidade. O Dialex faz essas mentes **pensarem juntas**.

---

## Pesquisa & Agradecimentos

### Artigos Fundamentais

| # | Paper | Autores | Ano | Contribuicao |
|---|-------|---------|-----|-------------|
| 1 | Conceptual Blending | Fauconnier & Turner | 2002 | Mecanismo cognitivo para estrutura emergente |
| 2 | Diversity Trumps Ability | Hong & Page | 2004 | Prova matematica: diverso > melhor |
| 3 | The Act of Creation | Koestler | 1964 | Colisao de frames incompativeis = criatividade |
| 4 | Agentic Deep Graph Reasoning | Buehler (MIT) | 2025 | Knowledge graphs auto-organizantes |
| 5 | DMAD: Diverse Multi-Agent Debate | Donkey et al. | 2025 | Diversidade cognitiva > diversidade de persona |
| 6 | Free-MAD: Consensus-Free Debate | Cui et al. | 2025 | Debate sem consenso forcado supera alternativas |
| 7 | Hegelian Dialectics for LLMs | Abdali et al. (Microsoft) | 2025 | Tese-Antitese-Sintese em LLMs |
| 8 | Mixture-of-Agents | Wang et al. (Together AI) | 2024 | Sintese multi-modelo > GPT-4 solo |
| 9 | Collective Intelligence Factor | Woolley et al. | 2010 | Fator "c" mensuravel em grupos |
| 10 | Paraconsistent Logic | Newton da Costa | 1960s+ | Logica onde contradicao nao e fatal |

### Agradecimentos

- **Alan Nicolas** — Criador do MMOS e da metodologia DNA Mental de 8 camadas que serve como pipeline upstream do Dialex
- A comunidade academica de multi-agent debate, logica paraconsistente e ciencia cognitiva cujo trabalho fundamenta este projeto

---

## Roadmap MVP

O MVP segue o principio: **lance a versao chata, prove que funciona, depois ganhe o direito de adicionar complexidade.** O "momento 10x" deve acontecer em menos de 2 minutos do primeiro uso.

### Timeline (12 semanas)

| Semana | Entregavel |
|--------|-----------|
| 1-2 | Schema SQLite + FTS5, CRUD de nos/arestas, esqueleto do CLI, ingestao MMOS |
| 3-4 | Decomposicao multi-perspectiva, recuperacao por subgrafo por mente, recuperacao round-aware |
| 5-7 | Motor de debate 3 fases com LiteLLM, mapeamento de tensoes, compressao multi-escala, sintese |
| 8-9 | Modo entrevista, avaliacao com juiz unico, comparacao com baseline |
| 10-11 | Polimento, tratamento de erros, testes, teste da hipotese nula |
| 12 | Dog-food em dominio real, coleta de dados para decisoes da v2 |

### O que o MVP Prova

- Conhecimento pode ser armazenado, conectado e recuperado como grafo
- Duas ou mais mentes produzem divergencia e sintese significativas
- O grafo se atualiza com resultados de debates (loop de feedback funciona)
- Modo entrevista agrega valor alem do debate
- **O sistema supera mensuravelmente um unico prompt bem elaborado** (ou nao, e sabemos disso)

### O que Fica para v2+

- Logica de Belnap com 4 valores (MVP usa confianca simples 0.0-1.0)
- Debate completo de 7 fases (3 fases bastam para comecar)
- Agente Inquisidor (MVP usa modelos diferentes + check basico de conformidade)
- Painel multi-juiz
- Consolidacao de memoria (A-MEM, associacoes criativas, esquecimento)
- Grafos de identidade dinamica

---

## Contribuindo

Contribuicoes sao muito bem-vindas! O projeto esta em fase inicial e precisa de ajuda em varias frentes.

### Como contribuir

```bash
# Fork e clone
git clone https://github.com/SEU-USUARIO/dialex.git
cd dialex

# Ambiente virtual
python -m venv .venv
source .venv/bin/activate

# Instale com dependencias de dev
pip install -e ".[dev]"

# Rode os testes
pytest

# Crie uma branch
git checkout -b feat/sua-feature
```

### Areas que precisam de ajuda

- Motor de debate core
- Camada de armazenamento do knowledge graph (SQLite+JSON)
- Interface CLI
- Documentacao multi-idioma (ES, ZH)
- Testes e benchmarks
- Integracoes com provedores LLM

### Convencao de commits

Usamos [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` — Funcionalidade nova
- `fix:` — Correcao de bug
- `docs:` — Documentacao
- `refactor:` — Refatoracao
- `test:` — Testes
- `chore:` — Manutencao

Detalhes completos em [CONTRIBUTING.md](CONTRIBUTING.md).

---

## Licenca

[MIT](LICENSE) — Use, modifique, distribua. Credite o projeto se achar justo.

---

<div align="center">

**Dialex** — Conhecimento que nenhuma mente produziria sozinha.

</div>
