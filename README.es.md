<p align="center">
  <h1 align="center">Dialex</h1>
  <p align="center"><strong>Amplificador Cognitivo de Búsqueda — Debate multi-mente que produce conocimiento emergente</strong></p>
</p>

<p align="center">
  <a href="README.md">English</a> ·
  <a href="README.pt-br.md">Português</a> ·
  <strong>Español</strong> ·
  <a href="README.zh-cn.md">简体中文</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License"></a>
  <a href="https://github.com/murilloimparavel/dialex"><img src="https://img.shields.io/badge/status-MVP-orange.svg" alt="Status: MVP"></a>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/python-3.11+-blue.svg" alt="Python 3.11+"></a>
</p>

---

## Qué es Dialex

**La metáfora:** Imaginen una mesa redonda donde los autores de libros discuten entre sí — y la discusión produce un libro nuevo que ninguno de ellos podría haber escrito solo.

Dialex es un sistema donde múltiples mentes expertas de IA — cada una con un método de razonamiento distinto — debaten problemas y producen conocimiento que ninguna mente individual podría generar por sí sola.

### Encuadre honesto

Dialex es un **amplificador cognitivo de búsqueda**. Usa múltiples lentes analíticos para explorar un espacio de problemas más ampliamente de lo que un solo prompt haría, combina los resultados a través de síntesis estructurada, y presenta hallazgos que resaltan divergencias, tensiones y combinaciones novedosas.

| Lo que sí es | Lo que no es |
|-------------|-------------|
| Diversidad funcional bajo restricciones | Mentes que "discrepan" genuinamente |
| Novedad combinatoria y estructural | Emergencia ontológica |
| Divergencia estructurada con síntesis | Debate existencial con identidades reales |
| Fidelidad de persona | Clonación cognitiva |

> El sistema debe superar un test de hipótesis nula: si no produce resultados mediblemente mejores que un solo LLM bien instruido con "analiza X desde múltiples perspectivas", la arquitectura no justifica su complejidad.

---

## Características principales

- **Motor de debate multi-mente** — Mentes con métodos de razonamiento distintos debaten problemas estructuradamente
- **Grafo de conocimiento auto-organizante** — SQLite + JSON que crece con cada debate; el conocimiento se acumula y conecta
- **Detección de emergencia en 3 niveles** — Síntesis productiva (L1), novedad conceptual (L2), emergencia estructural (L3)
- **Lógica de Belnap de 4 valores** — Las contradicciones no son errores, son la fuente más valiosa de conocimiento
- **Modelo bi-temporal** — Cada nodo de conocimiento tiene validez temporal y contexto histórico
- **Recuperación basada en tensión** — Busca no solo lo similar, sino lo productivamente diferente
- **Local-first** — Sin dependencias de infraestructura externa; SQLite + JSON + git

---

## Inicio rápido

> **Estado:** MVP en desarrollo activo. Las instrucciones se actualizarán conforme avance el proyecto.

```bash
# Clonar el repositorio
git clone https://github.com/murilloimparavel/dialex.git
cd dialex

# Crear entorno virtual
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate   # Windows

# Instalar dependencias
pip install -e ".[dev]"

# Ejecutar tests
pytest
```

---

## Arquitectura

Dialex opera en 5 capas:

```
┌─────────────────────────────────────────────┐
│  Capa 5: Motor de debate                    │
│  Selección de mentes · Rondas de debate     │
│  Síntesis · Detección de emergencia         │
├─────────────────────────────────────────────┤
│  Capa 4: Perfiles de identidad              │
│  Perfiles cognitivos por mente              │
│  Métodos de razonamiento · Voz DNA          │
├─────────────────────────────────────────────┤
│  Capa 3: Recuperación semántica             │
│  Búsqueda por tensión · Cross-mind          │
│  Contradicciones · Clusters                 │
├─────────────────────────────────────────────┤
│  Capa 2: Grafo de conocimiento              │
│  SQLite + JSON · Belnap 4-valued            │
│  Bi-temporal · Proveniencia                 │
├─────────────────────────────────────────────┤
│  Capa 1: Pipeline de ingestión              │
│  Parsing MMOS · Mapeo DNA Mental            │
│  Creación de nodos y aristas                │
└─────────────────────────────────────────────┘
```

### Tipos de nodos del grafo

| Tipo | Origen (Capa DNA Mental) |
|------|--------------------------|
| `pattern` | L1-L4: Patrones de comportamiento, comunicación, rutinas, reconocimiento |
| `mental_model` | L5: Modelos mentales y frameworks |
| `heuristic` | L4-L5: Reglas de decisión y atajos cognitivos |
| `value` / `belief` | L6-L7: Jerarquía de valores y obsesiones centrales |
| `contradiction` | L8: Paradojas productivas (la "capa de oro") |
| `synthesis` | Generado por debates — conocimiento emergente |

---

## La ciencia detrás

Dialex se fundamenta en 7 principios derivados de la investigación:

1. **Diversidad cognitiva** — La calidad de las soluciones mejora con la diversidad de métodos de razonamiento, no solo con la cantidad de agentes. Un debate entre 3 mentes con enfoques distintos supera a 10 mentes con el mismo enfoque.

2. **Tensión productiva** — Las contradicciones entre perspectivas son señales valiosas, no errores a resolver. Cuando dos mentes discrepan, esa tensión es exactamente donde se esconde el conocimiento más interesante.

3. **Lógica de Belnap (4 valores)** — `true`, `false`, `both`, `neither` — permite representar conocimiento contradictorio sin colapsar a una sola verdad. Un concepto puede ser simultáneamente verdadero y falso según diferentes marcos de referencia.

4. **Modelo bi-temporal** — Todo conocimiento tiene dos ejes temporales: cuándo es válido en el mundo y cuándo el sistema lo registró. Esto permite consultas como "qué creíamos sobre X en la fecha Y".

5. **Emergencia débil (Bedau)** — Lo que emerge es deducible en principio pero no en la práctica; la novedad viene de la recombinación, no de la magia. El sistema no inventa — descubre combinaciones que existían implícitamente.

6. **Decaimiento temporal** — El conocimiento tiene vida media; lo que no se usa pierde confianza gradualmente. La participación en debates renueva la relevancia de los nodos.

7. **Anti-sicofancia** — Mecanismos activos para evitar que las mentes converjan artificialmente hacia el consenso. El acuerdo fácil no produce conocimiento nuevo.

---

## Construido sobre MMOS

Dialex está construido sobre el **MMOS (Mind Mapping & Orchestration System)**, creado por **Alan Nicolas**.

MMOS es el sistema upstream que crea las mentes expertas a través de la metodología **DNA Mental** de 8 capas — un proceso riguroso que mapea patrones de comportamiento, estilos de comunicación, modelos mentales, valores, obsesiones y paradojas productivas de expertos de dominio.

Dialex toma estas mentes creadas por MMOS y les da algo que antes no tenían: la capacidad de **debatir entre sí** y producir conocimiento que trasciende a cualquier mente individual.

> **Créditos:** Alan Nicolas es el creador de MMOS y la metodología DNA Mental. Dialex extiende su trabajo hacia la inteligencia colectiva emergente.

---

## Investigación y reconocimientos

Este proyecto se basa en investigación extensa:

- **50+ papers académicos** analizados en la fase inicial de investigación por un equipo de 5 agentes especializados
- **35 frameworks candidatos** evaluados por 4 subagentes analistas (KARMA, TruthfulRAG, MAGMA, Graphiti, Kumiho, GKMAD, DoM/DoG, MAKGED, HippoRAG, Agentic-KGR, entre otros). De estos, 5 fueron absorbidos al MVP, 10 diferidos a v2, y 21 descartados
- **5 revisiones adversariales** desde perspectivas distintas (arquitecto pragmático, científico cognitivo, emprendedor de producto, red teamer, filósofo de la mente)
- **4 análisis de falla** con patrones SIF (Semantic Isolation Failure) identificados y mitigados

Influencias teóricas clave:

| Autor/Teoría | Contribución a Dialex |
|-------------|----------------------|
| Belnap (lógica de 4 valores) | Manejo de inconsistencia en bases de datos de conocimiento |
| Dung (frameworks de argumentación) | Estructura formal para debates entre agentes |
| Bedau (emergencia débil) | Marco teórico para definir y detectar novedad |
| Bakhtin (heteroglosia) | Diversidad de voces como fuente de significado |
| Schwartz (taxonomía de valores) | Clasificación de valores para nodos del grafo |
| Dreyfus (modelo de experticia) | Niveles de confianza en heurísticas |

---

## Roadmap MVP

| Fase | Alcance | Estado |
|------|---------|--------|
| **Fase 1** | Grafo de conocimiento base (SQLite + JSON, esquema bi-temporal) | En progreso |
| **Fase 2** | Pipeline de ingestión MMOS (parsing de artefactos, mapeo DNA Mental) | Planeado |
| **Fase 3** | Motor de debate (selección de mentes, rondas, síntesis) | Planeado |
| **Fase 4** | Detección de emergencia y ciclo de retroalimentación | Planeado |
| **Fase 5** | CLI y API de consulta | Planeado |

> **62 stories** definidas a lo largo de 5 epics. Consulten el [PRD completo](docs/prd/cognitive-knowledge-base-graph-prd.md) para todos los detalles.

---

## Contribuir

Las contribuciones son bienvenidas. Consulten [CONTRIBUTING.md](CONTRIBUTING.md) para la guía de configuración del entorno, convenciones de commits y áreas donde necesitamos ayuda.

Áreas prioritarias:
- Implementación del motor de debate central
- Capa de almacenamiento del grafo de conocimiento
- Interfaz CLI
- Testing y benchmarking
- Integraciones con proveedores de LLM

---

## Licencia

[MIT](LICENSE) — Libre para uso, modificación y distribución.

---

<p align="center">
  <sub>Dialex es un proyecto open-source. Construido con curiosidad y contradicciones productivas.</sub>
</p>
