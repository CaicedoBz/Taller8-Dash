# Taller 8 — Tablero en contenedor Docker

Imagen `bankchurn-dash` del curso **Proyecto: Desarrollo de Soluciones** (MAIA — Universidad de
los Andes). Tablero en Dash que consume la API de predicción de abandono a través de HTTP.

## Estructura

- `Dockerfile` — parte de `python:3.12-slim`, crea el usuario `dash-user`, instala las
  dependencias y arranca el tablero con `run.sh` (gunicorn). Expone el puerto 8050.
- `app/` — código del tablero (`app.py`) y sus dependencias.

## Uso

```bash
sudo docker build -t bankchurn-dash:latest .
sudo docker run -p 8050:8050 -it -e PORT=8050 -e API_URL=<IP> -e API_PORT=8001 bankchurn-dash
```

El tablero no contiene el modelo: arma la URL de la API con las variables de entorno `API_URL`
y `API_PORT`, y le envía las solicitudes de predicción por HTTP.
