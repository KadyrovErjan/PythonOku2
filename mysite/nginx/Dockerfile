FROM node:22-alpine AS frontend-build

WORKDIR /frontend
COPY frontend/package*.json ./
RUN npm ci
COPY frontend/ ./
RUN npm run build -- --configLoader runner

FROM nginx:1.27-alpine

COPY mysite/nginx/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=frontend-build /frontend/dist /usr/share/nginx/html
