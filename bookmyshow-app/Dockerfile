# Use Node.js for building
FROM node:18 AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Use Nginx to serve production build
FROM nginx:alpine
WORKDIR /usr/share/nginx/html
COPY --from=build /app/build ./

# Expose port 3000 (or 80 if you prefer)
EXPOSE 3000

# Replace default Nginx config if needed
CMD ["nginx", "-g", "daemon off;"]
