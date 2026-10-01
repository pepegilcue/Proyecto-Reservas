# Plataforma de reservas culturales - Despliegue con Docker

Actividad DAW UD01 RA1. Despliegue con Docker Compose de una plataforma de reservas (Nginx + API + base de datos).

> **Estado: trabajo en curso.** Esta es una entrega parcial. Abajo se indica lo hecho y lo pendiente.

## Arquitectura (prevista)

Cliente -> Nginx (puerto 80) -> API (puerto 3000, interno) -> MySQL (puerto 3306, interno) -> volumen `mysql_data`

- Unico puerto expuesto al host: 80 (Nginx).
- API y base de datos no publican puertos.
- Redes: `frontend` y `backend`.

## Estado

| Elemento | Estado |
|----------|--------|
| Estructura del repositorio | Hecho |
| `.env.example` / `.gitignore` / `.dockerignore` | Hecho |
| Servicio Nginx (Dockerfile + `default.conf`) | Hecho |
| Servicio MySQL con volumen persistente, sin puerto publicado | Hecho |
| Credenciales fuera del repositorio (`.env`) | Hecho |
| Servicio API (contenedor independiente) | Pendiente |
| Proxy Nginx -> API | Pendiente |
| Healthchecks | Pendiente |
| Pruebas HTTP y logs | Pendiente |
| Prueba de persistencia | Pendiente |
| Diagrama de arquitectura | Pendiente |

## Instalacion y arranque

```bash
git clone <URL_DEL_REPOSITORIO>
cd proyecto-reservas
cp .env.example .env     # editar las contrasenas
docker compose config    # validar el compose
docker compose up --build
```

Abrir http://localhost

## Parada

```bash
docker compose down      # conserva el volumen con los datos
```

## Pendiente para la siguiente entrega

- Anadir el servicio `api` y conectarlo con la base de datos.
- Configurar el proxy `/api/` en Nginx.
- Anadir healthchecks, pruebas con curl y logs.
- Demostrar la persistencia de datos tras recrear el contenedor de la BD.
- Completar documentacion e incidencias habituales.
