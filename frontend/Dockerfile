# ---------- Stage 1: Build Angular ----------
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

# ---------- Stage 2: Serve with Nginx ----------
FROM nginx:alpine

RUN rm -rf /usr/share/nginx/html/*

# Copy built Angular files
COPY --from=build /app/dist/angular-15-crud/ /usr/share/nginx/html

# 🔥 VERY IMPORTANT - copy nginx config
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]