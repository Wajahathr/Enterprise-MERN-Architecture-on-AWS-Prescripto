# Stage 1: Build Stage (Vite se static files generate karne ke liye)
FROM node:18-alpine AS builder

WORKDIR /app

# Dependencies copy aur install
COPY package*.json ./
RUN npm install

# Saara code copy kar ke build create karein
COPY . .
RUN npm run build

# Stage 2: Production Stage (Nginx par serve karne ke liye)
FROM nginx:alpine

# Stage 1 se banayi gayi 'dist' folder ko Nginx ki public directory mein copy karein
# Note: Vite default 'dist' folder banata hai. Agar CRA (React) ho toh 'build' hota hai.
COPY --from=builder /app/dist /usr/share/nginx/html

# Nginx default port 80 par chalta hai
EXPOSE 80

# Nginx ko background mein run karne ki command (alpine image mein default hoti hai, par explicitly likhna acha hai)
CMD ["nginx", "-g", "daemon off;"]