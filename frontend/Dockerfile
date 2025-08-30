# =========================================
# Stage 1: Build the Vue.js Application
# =========================================
ARG NODE_VERSION=22.19.0-alpine3.22
ARG NGINX_VERSION=stable-alpine

FROM node:${NODE_VERSION} AS builder
WORKDIR /app
COPY package*.json ./
RUN --mount=type=cache,target=/root/.npm npm ci

COPY . .
ENV NODE_OPTIONS=--openssl-legacy-provider
RUN npm run build -- --base=/momo-store/

# =========================================
# Stage 2: Prepare Nginx to Serve Static Files
# =========================================

FROM nginx:${NGINX_VERSION} AS runner

RUN mkdir -p /var/cache/nginx /var/run \
    && chown -R nginx:nginx /var/cache/nginx /var/run

COPY nginx.conf /etc/nginx/nginx.conf

COPY --chown=nginx:nginx --from=builder /app/dist /usr/share/nginx/html/momo-store

USER nginx
EXPOSE 8080

ENTRYPOINT ["nginx", "-c", "/etc/nginx/nginx.conf"]
CMD ["-g", "daemon off;"]