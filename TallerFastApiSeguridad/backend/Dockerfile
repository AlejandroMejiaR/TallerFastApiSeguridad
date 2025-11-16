# backend/Dockerfile

# --- Etapa 1: Imagen base ---
# Usamos una imagen oficial de Python. La etiqueta "slim" es más ligera.
FROM python:3.11-slim

# Establecemos el directorio de trabajo dentro del contenedor
WORKDIR /app

# --- Etapa 2: Instalar dependencias ---
# Copiamos solo el archivo de requerimientos primero para aprovechar el cache de Docker.
# Si no cambiamos los requerimientos, Docker no volverá a instalar todo.
COPY requirements.txt .
RUN pip install -r requirements.txt

# --- Etapa 3: Copiar el código de la aplicación ---
# Copiamos todo el contenido de la carpeta backend al directorio de trabajo /app en el contenedor
COPY . .

# --- Etapa 4: Comando de ejecución ---
# Le decimos a Docker cómo iniciar nuestra aplicación usando Gunicorn.
# Esto expone la app en el puerto 8000 DENTRO del contenedor.
# Usamos 0.0.0.0 para que sea accesible desde fuera del contenedor (por Nginx).
CMD ["gunicorn", "-w", "4", "-k", "uvicorn.workers.UvicornWorker", "main:app", "--bind", "0.0.0.0:8000"]