# ✏️ Excalidraw — Despliegue con Docker

**Excalidraw** es una pizarra virtual de código abierto con estilo de dibujo a mano alzada. Ideal para diagramas, esquemas, wireframes y brainstorming colaborativo. Todo el contenido se procesa localmente en el navegador — sin datos enviados a servidores externos.


## 📋 Requisitos previos

- [Docker](https://docs.docker.com/get-docker/) >= 20.10
- [Docker Compose](https://docs.docker.com/compose/install/) >= 2.0

## 🚀 Inicio rápido

### 1. Crear el archivo `docker-compose.yml`

```yaml
services:
  excalidraw:
    image: excalidraw/excalidraw:latest
    container_name: excalidraw-app
    restart: unless-stopped
    ports:
      - "5000:80"
```

### 2. Levantar el servicio

```bash
docker compose up -d
```

### 3. Acceder a la interfaz

```
http://localhost:5000
```

## ✏️ Características principales

| Función | Descripción |
|---|---|
| 🖊️ Dibujo a mano alzada | Estilo natural con formas, flechas, texto y colores |
| 📐 Herramientas de diseño | Rectángulos, elipses, líneas, diamantes, imágenes |
| 🔒 Privacidad total | Todo el procesamiento ocurre en el navegador |
| 💾 Exportación | PNG, SVG y formato `.excalidraw` nativo |
| 🌙 Modo oscuro | Interfaz adaptable al tema del sistema |
| ⌨️ Atajos de teclado | Flujo de trabajo rápido sin abandonar el teclado |

## 🛑 Gestión del servicio

```bash
# Detener el servicio
docker compose down

# Reiniciar
docker compose restart excalidraw

# Ver logs
docker compose logs -f excalidraw

# Actualizar la imagen
docker compose pull
docker compose up -d
```

## 🔧 Puertos

| Puerto | Uso |
|---|---|
| `5000` | Interfaz web de Excalidraw |

Para cambiar el puerto host:

```yaml
ports:
  - "PUERTO_DESEADO:80"
```

## 🔒 Proxy inverso con Caddy (opcional)

Para exponer Excalidraw con dominio propio y HTTPS automático:

```
draw.tudominio.com {
    reverse_proxy excalidraw-app:80
}
```

> Asegúrate de que el contenedor de Caddy y `excalidraw-app` estén en la misma red Docker.

## 🔗 Referencias

- [GitHub — excalidraw/excalidraw](https://github.com/excalidraw/excalidraw)
- [Docker Hub — excalidraw/excalidraw](https://hub.docker.com/r/excalidraw/excalidraw)
- [Demo oficial](https://excalidraw.com/)
