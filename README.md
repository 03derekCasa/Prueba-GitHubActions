# Actualización semanal del repositorio (GitHub Actions)

## 1. Descripción de la GitHub Action
Este repositorio incluye un workflow de GitHub Actions que ejecuta una actualización automática semanal.
La actualización consiste en regenerar el fichero `status/weekly-update.md` con la fecha/hora (UTC) del último run.

### ¿Qué problema resuelve?
- Mantiene trazabilidad y evidencia de mantenimiento periódico en el repositorio.
- Demuestra automatización básica.

### ¿En qué proyectos se puede usar?
- Proyectos que necesitan tareas programadas: limpieza, actualización de docs, verificación de dependencias, etc.

## 2. Ubicación del workflow
Ruta: `.github/workflows/weekly-update.yml`

## 3. Explicación paso a paso del workflow (YAML)
- name: nombre visible del workflow en la pestaña Actions.
- on:
  - schedule: dispara el workflow semanalmente (en UTC).
  - workflow_dispatch: permite ejecutarlo manualmente.
- permissions:
  - contents: write, necesario para poder hacer commit/push con GITHUB_TOKEN.
- jobs:
  - weekly_update: job principal.
- runs-on:
  - ubuntu-latest: version de Linux donde se corre el programa.
- steps:
  1) actions/checkout@v4: descarga el repo.
  2) Update weekly status file: crea/actualiza `status/weekly-update.md` con timestamp.
  3) Commit changes: configura identidad git, detecta cambios y si los hay hace commit y push.

## 4. Ejecución de la action
- Automática: semanalmente mediante `schedule` (UTC).
- Manual: pestaña Actions → Weekly Repository Update → Run workflow.
