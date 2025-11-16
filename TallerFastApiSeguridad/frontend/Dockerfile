# frontend/Dockerfile

# --- ETAPA 1: "Builder" - El Taller ---
FROM node:18-alpine AS builder

# Recibe el argumento NEXT_PUBLIC_API_URL desde docker-compose.yml
ARG NEXT_PUBLIC_API_URL
# Expónelo como una variable de entorno para que el proceso `npm run build` pueda verlo
ENV NEXT_PUBLIC_API_URL=$NEXT_PUBLIC_API_URL

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .

RUN npm run build

# --- ETAPA 2: "Runner" - El Producto Final ---
FROM node:18-alpine

WORKDIR /app

COPY --from=builder /app/.next ./.next
COPY --from=builder /app/public ./public
COPY --from=builder /app/package.json ./package.json
COPY --from=builder /app/node_modules ./node_modules

# También definimos la variable de entorno aquí para que esté disponible en tiempo de ejecución
# si alguna vez Next.js la necesita del lado del servidor.
ENV NEXT_PUBLIC_API_URL=$NEXT_PUBLIC_API_URL

EXPOSE 3000

CMD ["npm", "start"]