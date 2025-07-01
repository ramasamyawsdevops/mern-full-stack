# Use official Node.js LTS image
FROM node:18

# Set working directory in container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application source code
COPY . .

# Expose port 5000
EXPOSE 5000

# Default command
CMD ["npm", "start"]
