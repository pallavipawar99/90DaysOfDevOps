# -------- Stage 1: Build --------
FROM node:18-alpine AS builder

WORKDIR /app

COPY package.json .
RUN npm install --production

COPY . .

# -------- Stage 2: Runtime --------
FROM node:18-alpine

WORKDIR /app

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Copy only required files from builder
COPY --from=builder /app /app

# Change ownership
RUN chown -R appuser:appgroup /app

# Switch to non-root
USER appuser

CMD ["node", "app.js"]