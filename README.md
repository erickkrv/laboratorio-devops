# Laboratorio DevOps - Integración continua con GitHub Actions

![CI Flask](https://github.com/erickkrv/laboratorio-devops/actions/workflows/ci.yml/badge.svg)

## Descripción

Aplicación Flask sencilla utilizada para automatizar su validación con GitHub Actions.
Expone dos endpoints:

- `/`: devuelve el mensaje `{"mensaje": "Virtualizacion URL"}`.
- `/health`: permite verificar que la aplicación responde correctamente (`{"status": "ok"}`).

Cada `push`, `pull_request` o ejecución manual (`workflow_dispatch`) ejecuta el workflow **CI Flask**,
que instala las dependencias y corre las pruebas automáticas con Pytest.

## Herramientas utilizadas

- Git y GitHub
- GitHub Actions
- Visual Studio Code
- Python 3.12
- Flask
- Pytest

## Estructura

```
laboratorio-devops/
├── app.py
├── requirements.txt
├── test_app.py
├── .gitignore
└── .github/
    └── workflows/
        └── ci.yml
```

## Instalación

```bash
git clone https://github.com/erickkrv/laboratorio-devops.git
cd laboratorio-devops

# macOS
python3 -m venv .venv
source .venv/bin/activate

# Windows con Git Bash
py -3.12 -m venv .venv
source .venv/Scripts/activate

python -m pip install -r requirements.txt
```

## Ejecución

```bash
python app.py
```

Abrir en el navegador:

- http://localhost:5000 → `{"mensaje": "Virtualizacion URL"}`
- http://localhost:5000/health → `{"status": "ok"}`

> En macOS el puerto 5000 puede estar ocupado por AirPlay. En ese caso se puede usar otro puerto:
> `flask --app app run --port 5001`.

## Pruebas

```bash
python -m pytest -v
```

Resultado esperado:

```
test_app.py::test_inicio PASSED
test_app.py::test_health PASSED
2 passed
```

## Evidencia del workflow

El workflow se encuentra en `.github/workflows/ci.yml` y sus ejecuciones pueden consultarse en la pestaña
[Actions](https://github.com/erickkrv/laboratorio-devops/actions) del repositorio.

| Commit | Resultado |
|---|---|
| Configurar integracion continua | Satisfactorio |
| Modificar mensaje de inicio | Fallido: `test_inicio` esperaba "Virtualizacion URL" |
| Corregir mensaje de inicio | Satisfactorio |

## Integrante

- Erick Eduardo Rivas Avalos - 1116323
