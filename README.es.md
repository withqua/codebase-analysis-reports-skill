# Codebase Analysis Reports Skill

<p align="center">
  <a href="README.md">한국어</a> •
  <a href="README.en.md">English</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.zh.md">中文</a> •
  <a href="README.es.md">Español</a>
</p>

Una skill para Hermes Agent que genera informes de análisis de codebases de forma breve, legible y basada en evidencia.

Guía a Hermes para analizar una codebase, plugin, librería, framework o repositorio y producir dos artefactos.

1. `CODEBASE_ANALYSIS_HUMAN.html` — informe HTML autónomo con diseño estandarizado (modo oscuro/claro, responsivo, código resaltado, diagramas Mermaid, optimizado para impresión)
2. `CODEBASE_ANALYSIS_AGENT.md` — informe operativo markdown de handoff(traspaso) para otro agente de IA

## Reglas principales

- Primero entender la estructura del repo(repositorio) y el `entrypoint`(punto donde empieza la ejecución).
- Luego crear un component map(mapa de componentes).
- Después profundizar según el objetivo del usuario.
- Cada afirmación importante debe tener file path(ruta de archivo) y line anchor(referencia de línea).
- Informe humano (HTML) ≤ 30KB, informe agente (MD) ≤ 7KB según `wc -c`.
- No escribir problemas o riesgos sin evidencia.
- Lo no confirmado va en `Analysis Limits / Uncertainty`(límites/incertidumbre del análisis), no en suposiciones.
- Explicar términos no obvios al primer uso, por ejemplo `manifest`(archivo de configuración que informa al host el nombre, entradas, permisos y hooks de un programa/plugin).
- Mantener identificadores en inglés — funciones, campos, comandos — y añadir explicación corta entre paréntesis si ayuda.

## Instalación

Instalación desde repo público:

```bash
hermes skills install https://raw.githubusercontent.com/withqua/codebase-analysis-reports-skill/main/SKILL.md
```

Instalación manual:

```bash
git clone https://github.com/withqua/codebase-analysis-reports-skill.git
mkdir -p ~/.hermes/skills/software-development/codebase-analysis-reports
cp codebase-analysis-reports-skill/SKILL.md ~/.hermes/skills/software-development/codebase-analysis-reports/SKILL.md
```

Si Hermes ya está corriendo, usa `/reload-skills` o reinicia la CLI.

## Uso

```bash
hermes -s codebase-analysis-reports
```

En el chat:

```text
/skill codebase-analysis-reports
```

Ejemplo:

```text
Analiza /path/to/repo. Mi objetivo es entender la arquitectura de plugins y las partes reutilizables de esta codebase. Crea un informe humano y un informe de handoff para un agente de IA con ese propósito.
```

## Archivos

- `SKILL.md` — skill real de Hermes Agent
- `references/html-template.html` — plantilla HTML para informe humano (especificación de diseño)
- `README.md` — guía en coreano
- `README.en.md` — English guide
- `README.ja.md` — 日本語ガイド
- `README.zh.md` — 中文指南
- `README.es.md` — guía en español
- `LICENSE` — MIT License
