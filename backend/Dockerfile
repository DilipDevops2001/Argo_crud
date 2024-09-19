# Use the latest stable Alpine Node.js image
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json (if available) first to leverage Docker cache
COPY package*.json ./

# Install dependencies only (using --production for smaller image)
RUN npm install --production

# Copy the rest of the application
COPY . .

# Expose the port the application will run on
EXPOSE 3333

# Add a health check to monitor the container's health (optional)
HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
    CMD curl --fail http://localhost:3333/ || exit 1

# Start the Node.js application
CMD ["npm", "start"]

