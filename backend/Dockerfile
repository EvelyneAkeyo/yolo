# Base image
FROM node:18-slim

# Create app directory
WORKDIR /app

# Copy dependency files and install
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Expose backend port
EXPOSE 5000

# Start the app
CMD ["node", "server.js"]