# ----------------------------
# STAGE 1:
# ----------------------------
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
# ----------------------------
# STAGE 2: 
# ----------------------------
FROM node:18-alpine
WORKDIR /app
USER node
COPY --from=builder /app/node_modules ./node_modules
COPY --chown=node:node . .
EXPOSE 3500
CMD ["node", "server.js"]
