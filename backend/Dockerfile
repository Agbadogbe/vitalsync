# ── Stage 1 : Tests & dépendances ──────────────────────────────
FROM node:20-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN ./node_modules/.bin/jest test/health.test.js --passWithNoTests

# ── Stage 2 : Image de production légère ───────────────────────
FROM node:20-alpine AS production

WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev
COPY --from=builder /app/server.js ./

EXPOSE 3000
USER node
CMD ["node", "server.js"]