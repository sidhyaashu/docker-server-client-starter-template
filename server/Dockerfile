# Use Node.js image
FROM node:18-alpine

# Set the working directory for the Express server
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the Express server files
COPY . .

# Expose port 4000 for the Express server
EXPOSE 4000

# Run the Express server
CMD ["node", "index.js"]
